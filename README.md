# Laravel Backblaze B2

[![Author](http://img.shields.io/badge/author-@marc_andre-blue.svg?style=flat-square)](https://twitter.com/marc_andre)
[![Latest Version on Packagist](https://img.shields.io/packagist/v/marcandreappel/laravel-backblaze-b2.svg?style=flat-square)](https://packagist.org/packages/gliterd/laravel-backblaze-b2)
[![Software License][ico-license]](LICENSE.md)
[![Total Downloads](https://img.shields.io/packagist/dt/marcandreappel/laravel-backblaze-b2.svg?style=flat-square)](https://packagist.org/packages/gliterd/laravel-backblaze-b2)

Visit (https://secure.backblaze.com/b2_buckets.htm) and get your account id and application key.

This package allows Laravel to use Backblaze B2 buckets as filesystem.
It uses the [Backblaze B2 SDK](https://github.com/gliterd/backblaze-b2) and the [Backblaze Flysystem Adapter](https://github.com/marcandreappel/flysystem-backblaze) to communicate with the API.

## Install

Via Composer

``` bash
composer require marcandreappel/laravel-backblaze-b2
```

## Configuration

In your `config/app.php`, add to the list of service providers:

``` php
\MarcAndreAppel\BackblazeB2\BackblazeB2ServiceProvider::class,
```

In your `config/filesystems.php` add under disks the driver:
```php
        'b2' => [
            'driver'         => 'b2',
            'accountId'      => env('B2_APPLICATION_KEY_ID'),
            'applicationKey' => env('B2_APPLICATION_KEY_SECRET'),
            'bucketName'     => env('B2_BUCKET_NAME'),
            'bucketId'       => env('B2_BUCKET_ID', ''),
        ],
```

## Using ApplicationKey instead of MasterKey

If you specify only the `$bucketName` when creating the BackblazeAdapter, your `$applicationKey` must be the **master key**.
However, if you specify both bucket name and bucket id, you can use an application key.
Fetch your `$bucketId` using the [b2 command line tool](https://www.backblaze.com/b2/docs/quick_command_line.html) `b2 get-bucket <bucketName>`.

## Usage

Use it directly with the `Storage` facade.

``` php
\Storage::disk('b2')->put('filename.txt', 'My important content');
\Storage::disk('b2')->get('filename.txt')
```

## Security

If you discover any security related issues, please use the issue tracker.

## Credits

- [Ramesh Mhetre][link-author]
- [All Contributors][link-contributors]

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

[ico-version]: https://img.shields.io/packagist/v/marcandreappel/laravel-backblaze-b2.svg?style=flat-square
[ico-license]: https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square
[ico-downloads]: https://img.shields.io/packagist/dt/marcandreappel/laravel-backblaze-b2.svg?style=flat-square

[link-packagist]: https://packagist.org/packages/marcandreappel/laravel-backblaze-b2
[link-downloads]: https://packagist.org/packages/marcandreappel/laravel-backblaze-b2
[link-author]: https://github.com/mhetreramesh
[link-contributors]: ../../contributors
