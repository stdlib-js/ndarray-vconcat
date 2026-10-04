<!--

@license Apache-2.0

Copyright (c) 2026 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# vconcat

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Concatenate a list of [ndarrays][@stdlib/ndarray/ctor] along the second-to-last dimension.

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

</section>

<!-- /.intro -->

<!-- Package usage documentation. -->



<section class="usage">

## Usage

```javascript
import vconcat from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-vconcat@deno/mod.js';
```

You can also import the following named exports from the package:

```javascript
import { assign } from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-vconcat@deno/mod.js';
```

#### vconcat( arrays )

Concatenates a list of [ndarrays][@stdlib/ndarray/ctor] along the second-to-last dimension.

```javascript
import array from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-array@deno/mod.js';

var x = array( [ [ 1.0, 2.0 ], [ 3.0, 4.0 ] ] );
// returns <ndarray>[ [ 1.0, 2.0 ], [ 3.0, 4.0 ] ]

var y = array( [ [ 5.0, 6.0 ], [ 7.0, 8.0 ], [ 9.0, 10.0 ] ] );
// returns <ndarray>[ [ 5.0, 6.0 ], [ 7.0, 8.0 ], [ 9.0, 10.0 ] ]

var out = vconcat( [ x, y ] );
// returns <ndarray>[ [ 1.0, 2.0 ], [ 3.0, 4.0 ], [ 5.0, 6.0 ], [ 7.0, 8.0 ], [ 9.0, 10.0 ] ]
```

The function accepts the following arguments:

-   **arrays**: a list of input [ndarrays][@stdlib/ndarray/ctor]. The data type of the output [ndarray][@stdlib/ndarray/ctor] is determined by applying [type promotion rules][@stdlib/ndarray/promotion-rules] to the list of input [ndarrays][@stdlib/ndarray/ctor]. If provided [ndarrays][@stdlib/ndarray/ctor] having different [memory layouts][@stdlib/ndarray/orders], the output [ndarray][@stdlib/ndarray/ctor] has the [default order][@stdlib/ndarray/defaults].

#### vconcat.assign( arrays, out )

Concatenates a list of [ndarrays][@stdlib/ndarray/ctor] along the second-to-last dimension and assigns results to a provided output [ndarray][@stdlib/ndarray/ctor].

```javascript
import array from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-array@deno/mod.js';
import zeros from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-zeros@deno/mod.js';

var x = array( [ [ 1.0, 2.0 ], [ 3.0, 4.0 ] ] );
// returns <ndarray>[ [ 1.0, 2.0 ], [ 3.0, 4.0 ] ]

var y = array( [ [ 5.0, 6.0 ], [ 7.0, 8.0 ], [ 9.0, 10.0 ] ] );
// returns <ndarray>[ [ 5.0, 6.0 ], [ 7.0, 8.0 ], [ 9.0, 10.0 ] ]

var z = zeros( [ 5, 2 ] );
// returns <ndarray>[ [ 0.0, 0.0 ], [ 0.0, 0.0 ], [ 0.0, 0.0 ], [ 0.0, 0.0 ], [ 0.0, 0.0 ] ]

var out = vconcat.assign( [ x, y ], z );
// returns <ndarray>[ [ 1.0, 2.0 ], [ 3.0, 4.0 ], [ 5.0, 6.0 ], [ 7.0, 8.0 ], [ 9.0, 10.0 ] ]

var bool = ( out === z );
// returns true
```

The function accepts the following arguments:

-   **arrays**: a list of input [ndarrays][@stdlib/ndarray/ctor]. Must [promote][@stdlib/ndarray/promotion-rules] to a [data type][@stdlib/ndarray/dtypes] which can be (mostly) [safely cast][@stdlib/ndarray/mostly-safe-casts] to the [data type][@stdlib/ndarray/dtypes] of the output [ndarray][@stdlib/ndarray/ctor].
-   **out**: output [ndarray][@stdlib/ndarray/ctor].

</section>

<!-- /.usage -->

<!-- Package usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

-   Input [ndarrays][@stdlib/ndarray/ctor] must have more than one dimension.

</section>

<!-- /.notes -->

<!-- Package usage examples. -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
import discreteUniform from 'https://cdn.jsdelivr.net/gh/stdlib-js/random-discrete-uniform@deno/mod.js';
import ndarray2array from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-to-array@deno/mod.js';
import vconcat from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-vconcat@deno/mod.js';

var x = discreteUniform( [ 2, 3 ], 0, 10, {
    'dtype': 'generic'
});
console.log( ndarray2array( x ) );

var y = discreteUniform( [ 3, 3 ], 0, 10, {
    'dtype': 'generic'
});
console.log( ndarray2array( y ) );

var out = vconcat( [ x, y ] );
console.log( ndarray2array( out ) );
```

</section>

<!-- /.examples -->

<!-- Section to include cited references. If references are included, add a horizontal rule *before* the section. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="references">

</section>

<!-- /.references -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2026. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/ndarray-vconcat.svg
[npm-url]: https://npmjs.org/package/@stdlib/ndarray-vconcat

[test-image]: https://github.com/stdlib-js/ndarray-vconcat/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/ndarray-vconcat/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/ndarray-vconcat/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/ndarray-vconcat?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/ndarray-vconcat.svg
[dependencies-url]: https://david-dm.org/stdlib-js/ndarray-vconcat/main

-->

[chat-image]: https://img.shields.io/badge/zulip-join_chat-brightgreen.svg
[chat-url]: https://stdlib.zulipchat.com

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/ndarray-vconcat/tree/deno
[deno-readme]: https://github.com/stdlib-js/ndarray-vconcat/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/ndarray-vconcat/tree/umd
[umd-readme]: https://github.com/stdlib-js/ndarray-vconcat/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/ndarray-vconcat/tree/esm
[esm-readme]: https://github.com/stdlib-js/ndarray-vconcat/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/ndarray-vconcat/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/ndarray-vconcat/main/LICENSE

[@stdlib/ndarray/ctor]: https://github.com/stdlib-js/ndarray-ctor/tree/deno

[@stdlib/ndarray/dtypes]: https://github.com/stdlib-js/ndarray-dtypes/tree/deno

[@stdlib/ndarray/orders]: https://github.com/stdlib-js/ndarray-orders/tree/deno

[@stdlib/ndarray/defaults]: https://github.com/stdlib-js/ndarray-defaults/tree/deno

[@stdlib/ndarray/promotion-rules]: https://github.com/stdlib-js/ndarray-promotion-rules/tree/deno

[@stdlib/ndarray/mostly-safe-casts]: https://github.com/stdlib-js/ndarray-mostly-safe-casts/tree/deno

</section>

<!-- /.links -->
