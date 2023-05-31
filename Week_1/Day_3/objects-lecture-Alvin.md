#Objects Lecture


Today we looked into objects, what are they, how to use them, how to send them and return from functions

So far during your bootcamp life, you have been using things such as primatve types and arrays

Review (Primative Types)

There are 7 primitive data types: string, number, bigint, boolean, null, undefined, and symbol.

let str = 'Hello World'; // string
let num = 28; // number
let bigInt = 9007199254740991n; // big int
let bool = true; // boolean
let sym = Symbol('Sym'); // Symbol <--- we haven't tried it
let nothing = null;
let noExistance = undefined;
Quick 0, null, undefined meme


Review ( Arrays )

An array is a special variable, which can hold more than one value at a time.

If you have a list of items (a list of car names, for example), storing the cars in single variables could look like this:

let carsNames = ['Toyota', 'Honda', 'Mitsubishi', 'BMW'];
Now here is a new problem we are facing. We are trying to record the following infomration of a car:

brand
model
year
transmission type
Theoretically, we can just store that information into an array and be done with it

let car = ['toyota', 'GT86', 2019, 'manual'];
....BUT the problem with this is that people and other programs that use this array will have to remember that the brand name is always at the 0 element and model will the 1 element of the array, etc...

Enter Objects

An object, just like an array, can hold more than 1 value at a time. The differences are:

value MUST have a specific key.
Objects are denotes with {} brackets
let car = {
  brand: 'toyota',
  model: 'GT86',
  year: 2019,
  transmissionType: 'manual',
};
To get the brand value out of the object we can use the dot notation.

car.brand; // gets the brand
We also can set a new value or overwrite the existing value with the dot notation

car.brand = 'Subaru'; // overwrote the brand with a name Subaru
car.model = 'BRZ'; // overwrote model with name BRZ
car.driveterain = 'RWD'; // added a new driveterain key with value RWD
very simular to arrays but more descriptive. Here's how it will look like in arrays.

car[0]; // WAY less descriptive. What was at the 0th index again??
The advantage to using objects is that the order of the keys does not infact matter, because you can call them each key name.

Cool!! What else can objects store othar than primative types?

Well, objects can store anything! We can store arrays as values

let car = {
  brand: 'toyota',
  model: 'GT86',
  year: 2019,
  transmissionType: 'manual',
  colors: ['red', 'black', 'green', 'white', 'baby blue', 'grey'], // the value is a whole array
};
To access the colors array we write

car.colors; // returns the array of all the colors
if we want to get the first element:

car.colors[0]; // red
What if we want to loop through the array?

for (let color of car.colors) {
  console.log(color);
}

// OUTPUT
('red');
('black');
('green');
('white');
('baby blue');
('grey');
Object within an Object (Object-ception)

We can also put other objects into the object.

let car = {
  brand: 'toyota',
  model: 'GT86',
  year: 2019,
  transmissionType: 'manual',
  colors: ['red', 'black', 'green', 'white', 'baby blue', 'grey'],
  //INCOMING NEW OBJECT
  driver: {
    name: 'Vasiliy',
    rank: 'amateur',
    bloodType: 'O-',
  },
};
To access the driver rank (nested object) we would write:

car.driver.rank; // amateur
Functions inside of Object

We can even create FUNCTIONS inside of our Object.

let car = {
  brand: 'toyota',
  model: 'GT86',
  year: 2019,
  transmissionType: 'manual',
  colors: ['red', 'black', 'green', 'white', 'baby blue', 'grey'],
  driver: {
    name: 'Vasiliy',
    rank: 'amateur',
    bloodType: 'O-',
  },
  // A function in our car object
  noise: function () {
    console.log('BRrrrrbrbrbrbrbrbrbrbrbrrbrbrbrb');
  },
};
To call the function:

car.noise(); // Runs the noise function from the car object
What if we need to write a function that needs access to one or more object keys/values ???

Enter the this keyword. this refers to the context of the object we are in. We can access all the object values and keys with the keyword this.

In the function printSpecs() we get the brand and model by using the this keyword.

let car = {
  brand: 'toyota',
  model: 'GT86',
  year: 2019,
  transmissionType: 'manual',
  colors: ['red', 'black', 'green', 'white', 'baby blue', 'grey'],
  driver: {
    name: 'Vasiliy',
    rank: 'amateur',
    bloodType: 'O-',
  },
  noise: function () {
    console.log('BRrrrrbrbrbrbrbrbrbrbrbrrbrbrbrb');
  },
  printSpecs() {
    console.log('CAR: ' + this.brand + ' ' + this.model);
    console.log('Driver: ' + this.driver.name, this.driver.bloodType);
    console.log('The car Makes:');
    this.noise();
  },
};
Other cool things you can do with Objects

let batman = {
  realName: 'Bruce Wayne',
  suit: 'Mark 2',
  gadgets: [],
};
// Make a function that adds a new gadget
// to the the batman object. The batman object
// will be passed into our function..
const addGadget = function (gadgetName, obj) {
  obj.gadgets.push(gadgetName);
};
We can pass objects into a function and change specific values. Because the object is passed by memory address it effects the object that we passed. (Note how we did this with primative types for the swap function and nothing happened!)

We can loop through all keys and print out spefic values from it.

let shoppingCart = {
  four: 'SPAM',
  6: 'folders',
  two: 'Brush',
  one: 'Toothpaste',
  three: 'toilet paper',
  7: 'Chrismas Tree',
  five: 'toilet brush',
};

// I want to print each item (value) in our object

const printCart = function (cart) {
  // console.log(cart);
  // I want to loop over an object
  // METHOD 1 --- Using the IN
  for (let item in cart) {
    console.log(cart[item]);
  }
  // METHOD 2 -
  // let values = Object.values(cart);
  // console.log(values);
  // for (let item of values) {
  //   console.log(item);
  // }
  // METHOD 3
  // let keys = Object.keys(cart);
  // // console.log(keys);
  // for (let key of keys) {
  //   console.log(cart[key]);

  // }
  // console.log(key);
};
