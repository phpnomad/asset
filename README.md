# phpnomad/asset

[![Latest Version](https://img.shields.io/packagist/v/phpnomad/asset.svg)](https://packagist.org/packages/phpnomad/asset)
[![Total Downloads](https://img.shields.io/packagist/dt/phpnomad/asset.svg)](https://packagist.org/packages/phpnomad/asset)
[![PHP Version](https://img.shields.io/packagist/php-v/phpnomad/asset.svg)](https://packagist.org/packages/phpnomad/asset)
[![License](https://img.shields.io/packagist/l/phpnomad/asset.svg)](https://packagist.org/packages/phpnomad/asset)

`phpnomad/asset` defines the contract PHPNomad applications use to turn asset file paths into public URLs. The URL for a CSS file, an image, or a JavaScript bundle depends on where the code runs. A WordPress plugin, a Laravel app, and a standalone PHP service all publish assets under different prefixes. This package provides a single interface so the rest of your code can ask for an asset URL without caring which host is serving it.

## Installation

```bash
composer require phpnomad/asset
```

## Overview

- `PHPNomad\Asset\Interfaces\AssetStrategy` is the only interface in the package. It has two methods.
- `getUrlForAbsoluteAsset(string $file)` takes the absolute filesystem path to an asset and returns its public URL.
- `getUrlForRelativeAsset(string $file, string $relativeTo)` resolves a path relative to another file (usually `__FILE__` from the caller) and returns the URL for the resulting asset.
- Implementations live in host-specific integrations. The WordPress integration converts plugin paths through `plugin_dir_url()`. A standalone implementation strips a known public directory and joins the app URL.
- Swapping implementations lets the same asset-loading code move between hosts without changes.

## Documentation

Full documentation lives at [phpnomad.com](https://phpnomad.com).

## License

Released under the MIT License. See [LICENSE.txt](LICENSE.txt).
