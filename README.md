# dither (modified for Gopy)

This is a modified version of [dither](https://github.com/makew0rld/dither) Go library, made specifically to ease up process of writting bindings with [Gopy](https://github.com/go-python/gopy).

> **Note**
> If you are looking for Python bindings of dither library, check out [dither-go]() repository.

## Limitations:
* `PixelMapper` type and assosiated with this type functions are privated, as they aren't currently supported by Gopy 
<br>
(related PR: [#282](https://github.com/go-python/gopy/pull/282))
* You can't reuse generated `PixelMapper` assosiated functions, because of above limitation
* Any function that returnes more that one return value, is either privated or ignored during binding generation

## Changed structures:
* [`pixelmappers.go`](./pixelmappers.go):
    * `PixelMapper` type privated
    * `RandomNoiseGrayscale`, `RandomNoiseRGB`, `Bayer` and `PixelMapperFromMatrix` functions privated
* [`dither.go`](./dither.go):
    * `Mapper` field in `Ditherer` struct privated
    * New `SetBayer`, `SetOrdered`, `SetRandomGrayscale`, `SetRandomRGB` and `ClearMapper` helper functions

## TODO:
* Make a struct for `*Config` and `Offset` functions allowing to return multiple values using only one return value

## License
This repository is licensed under the same terms as the original library, which is licensed under the Mozilla Public License Version 2.0.
