# Magento 2 removal of all third party bundled modules

This repository contains a composer meta-package that removes third party bundled modules.

## Installation

To install, use the following command with your Magento2 version:

```
composer require yireo/magento2-replace-bundled:2.3.*
```

_Replace `*` with your magento version_

## Requiments

This package support Magento 2.3 or higher.

## Notes

See also the package [`yireo/magento2-replace-all`.](https://github.com/yireo/magento2-replace-all)

### Exception when editing products
When you have installed this extension, the `Temando_Shipping` module is removed. However, this extension might have added an EAV attribute already with a specific source model that no longer exists. This could generate an exception `Class Temando\Shipping\Model\Source\PackagingType does not exist`. To fix this, run the following SQL query in your database:

```sql
DELETE FROM `eav_attribute` WHERE `source_model` LIKE '%Temando%' 
```
