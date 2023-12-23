# Typescript Code Guide
Pastikan perangkat sudah install typescript secara global\
Untuk Inisialisasi awal ketik `tsc --init`\
Compile Typescript ke Javascript ketik: `tsc`\
konfigurasi rootDir dan outDir bisa dilakukan di tsconfig.ts
&nbsp;
## BASIC
### Variable
```
let sales:number = 123456_9842;
let course:string = "Hello";
let is_published:boolean = true;
```
### Array
```
let numberz; // array can insert various type of data
let numbers: number[] = [] // Explicitly define array only accept number data type
numbers[0] = 3
numbers[0] = 100
```
### Tuple
```
let user: [number, string, boolean, number] = [1, 'Madam', true, 0];
```
### Enum
```
const small = 1;
const medium = 3;
const hard = 27;

// Use PascalCase
const enum Size { Small= 1, Medium, Large}
let mySize: Size = Size.Medium;
console.log(mySize);
```
### Function
```
function calculateTax(income: number, tax: number): number {
    return 0;
}
// : number (1) = ensure parameter type number 
// : number (2) = ensure function returning number
```
### Object
```
let employee: {
    readonly id: number;
    name: string;
    retire: (date: Date) => void;
} = {
    id: 1,
    name: 'Madam',
    retire: (date: Date) => {
        console.log(date);
    }
}
```
&nbsp;
## ADVANCED
### Type Aliase
If someone want to make other object they need to define like this, that was terrible and not good for long term. Cz make our code hard to understand
```
let employee: {
    readonly id: number;
    name: string;
    retire: (date: Date) => void;
} = {
    id: 1,
    name: 'Madam',
    retire: (date: Date) => {
        console.log(date);
    }
}
```
So to solve the problem we use type instead, ex:
```
type Employee = {
    readonly id: number,
    name: string,
    retire: (date: Date) => void
}

let employee: Employee = {
    id: 1,
    name: "Hello",
    retire: (date: Date) => {
        console.log(date);
    }
}
```
### Union Type
```
function kgToLbs(weight: number | string): number {
    if(typeof weight === 'number')
        return weight * 2.2;
    else
        return parseInt(weight) * 2.2;
}
kgToLbs(10);
kgToLbs('10');
```
### Intersection Type
```
type Draggable = {
    drag: () => void;
};

type Resizable = {
    resize: () => void;
};

type UIWidget = Draggable & Resizable;

let textBox: UIWidget = {
    drag: () => {},
    resize: () => {}
}
```
### Literal Type
```
type Quantity = 50 | 100;
let quantity: Quantity = 100
```
### Nullable Type
```
function greet(name: string | null | undefined) {
    if (name)
        console.log(name.toUpperCase());
    else
        console.log('HOLa');
}
greet(undefined);
```
### Optional Chaining
```
type Customer = {
    birthday: Date
}

function getCustomer(id: number): Customer | null {
    return id === 0 ? null : { birthday: new Date() }
}

let customer = getCustomer(1)
console.log(customer?.birthday.getFullYear()); // optional property access operator

let log:any = null;
log?.('a');
```
 
