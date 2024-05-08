# @swenkerorg/molestiae-temporibus-accusamus

Roll calculator functions.

This module was created for calculating dimesions of materials in rolls for inventory and winding machines.

## Install

```sh
npm install @swenkerorg/molestiae-temporibus-accusamus
```

## Usage

```js
import { rollSolve } from '@swenkerorg/molestiae-temporibus-accusamus';

const materialHeight = 0.06;
const innerDiameter = 18;
const outerDiameter = 60;
const length = rollSolve(materialHeight, innerDiameter, outerDiameter);

console.log(length);
//=> 42882.74547004675
```

## API

### `function rollLength(h: number, d0: number, d1: number): number | undefined`

Calculates length of a roll (2D spiral).

Equations from https://www.giangrandi.ch/soft/spiral/spiral.shtml

```js
import { rollLength } from '@swenkerorg/molestiae-temporibus-accusamus';

const materialHeight = 0.1;
const innerDiameter = 2;
const outerDiameter = 3;
const length = rollLength(materialHeight, innerDiameter, outerDiameter);

console.log(length);
//=> 39.27313461871492
```

### `function rollOuterDiameter(h: number, d0: number, l: number, maxIter?: number): number | undefined`

Calcuates the outer diameter of a roll (2D spiral).

```js
import { rollOuterDiameter } from '@swenkerorg/molestiae-temporibus-accusamus';

const materialHeight = 0.1;
const innerDiameter = 2;
const length = 39.273_134_62;
const outerDiameter = rollOuterDiameter(materialHeight, innerDiameter, length);

console.log(outerDiameter);
//=> 3.0000000000272684
```

### `function rollInnerDiameter(h: number, d1: number, l: number): number | undefined`

Calculates the inner diameter of a roll (2D spiral).

```js
import { rollInnerDiameter } from '@swenkerorg/molestiae-temporibus-accusamus';

const materialHeight = 0.1;
const outerDiameter = 3;
const length = 39.273_134_62;
const innerDiameter = rollInnerDiameter(materialHeight, innerDiameter, length);

console.log(innerDiameter);
//=> 1.999999999959101
```

### `rollMaterialHeight(d0: number, d1: number, l: number): number | undefined`

Calculates the nominal material height or thickness in a roll (2D Spiral).

Equations from:
> Thickness of Material on a Roll Winding: Machines, Mechanics and Measurements
By James K. Good, David R. Roisum
page 124

```js
import { rollMaterialHeight } from '@swenkerorg/molestiae-temporibus-accusamus';

const innerDiameter = 2;
const outerDiameter = 3;
const length = 39.273_134_62;
const materialHeight = rollMaterialHeight(innerDiameter, outerDiameter, length);

console.log(materialHeight);
//=> 0.09999178458720241
```

### `function rollSolve(h?: number, d0?: number, d1?: number, l?: number): number | undefined`

Solves one missing dimension of a roll (2D spiral).

Pass in at least three arguments to solve for the fourth.

```js
import { rollSolve } from '@swenkerorg/molestiae-temporibus-accusamus';

const materialHeight = 0.06;
const innerDiameter = 18;
const outerDiameter = 60;
const length = rollSolve(materialHeight, innerDiameter, outerDiameter, undefined);

console.log(length);
//=> 42882.74547004675
```
