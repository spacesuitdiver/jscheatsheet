# JavaScript Cheat Sheet

## Basics
### VARIABLES
#### Defining
```javascript
var myString = 'Hello World';
var myNumber = 42; // the meaning of life of course
var myBoolean = true;
```

### ARRAYS
#### Defining
```javascript
var myArray = ['Value 1', 'Value 2', 'Value 3'];
```

#### Retrieving a value
```javascript
myArray[1]; // outputs "Value 2"
```

#### Retriving length
```javascript
myArray.length; // outputs 3
```

#### Iterating (using `for`)
```javascript
for (i = 0; i < myArray.length; i++) {
  console.log(i); // logs the current interation's index

  var someValueFromArray = myArray[i]; // stores the array value in a variable
  console.log(someValueFromArray); // logs the array value

  // ... additional repeating code here
}
```

#### Iterating (using `forEach`)
```javascript
myArray.forEach(function(myValue, myIndex) {
  console.log(myValue); // logs the array value
  console.log(myIndex); // logs the current interation's index
});
```

#### Searching (by value)
```javascript
var foundIndex = myArray.indexOf('Value 2'); // stores the found index in a variable
var foundValue = myArray[foundIndex]; // store the found value in a variable
console.log(foundIndex, foundValue); // logs both the index and value (`console.log` supports infinite arguments)
```

#### Searching (for non-existence)
```javascript
var foundIndex = myArray.indexOf('Something Not Here'); // stores the found index in a variable
if (foundIndex === -1) {
  console.log('not here'); // logs not here
}
```

#### Adding to (`push()`)
```javascript
myArray.push('Value 4');
// note the above line does not require an variable additional assignment
console.log(myArray); // logs "['Value 1', 'Value 2', 'Value 3', 'Value 4']"
```

#### Adding to (`concat()`)
```javascript
var someOtherArray = ['Value 4'];
myArray = myArray.concat(someOtherArray);
myArray = myArray.concat(['Value 5']);
// note the above line requires an additional variable assignment (`myArray = ...`)
// also note you pass an array into concat() instead of a value
console.log(myArray); // logs "['Value 1', 'Value 2', 'Value 3', 'Value 4', 'Value 5']"
```


### OBJECTS
#### Defining
```javascript
var car = { // define our object with the below properties and values
  make: 'Volkswagen', // defines a string
  model: 'Jetta',
  year: 2006, // defines a number
  odometer: 41077, // ALOTT ;)
  'fuel type': 'Gasoline', // defines a string with a property including a space
  checkEngineLightOn: true, // defines a boolean
  fixCar: function () { // defines a function (known as an object's "method")
    this.checkEngineLightOn = false; 
    // the use of `this` above is how we can modify object values from an objects function/method
  },
  drive: function (tripDistance) {
    this.odometer = this.odometer + tripDistance; // add our trip's distnace to our car's odometer
  },
  clean: function(wash, wax, vacuum) {
    var message = "You've "; // initialize a string for us to concatenate values onto
    if (wash) {
      message = message + 'washed '; // concat the word washed to the message
    }
    if (wax) {
      message = message + 'waxed ';
    }
    if (vacuum) {
      message = message + 'vacuumed ';
    }
    message = mesage + 'your car.';

    return message; // returns "You've washed waxed vacuumed your car." if all values are true.
  }
};
```

#### Assigning values (using dot notation)
```javascript
car.make = 'Nissan'; // Changes the make property from 'Volkswagen' to 'Nissan'
```

#### Assigning values (using `[]` aka brackets**) 
```javascript
car['fuel type'] = 'Diesel'; // needed for properties with spaces
```

#### Retrieving a value
```javascript
var myYear = car.year; // stores the car's year in a variable named `myYear`
console.log(year); // logs the cars year 2006
```

#### Executing a method
```javascript
car.fixCar(); // executes the `fixCar` method thus setting the check engine light to false (turning it off)
```

#### Executing a method (arguments)
```javascript
car.drive(100); // executes the `drive` method thus adding 100 miles to the odometer
```

#### Executing a method (multiple arguments)
```javascript
var myCarsCleanliness = car.clean(true, false, false); // executes and stores the `clean` (performing only a wash, the first argument) method's return value in a variable `myCarsCleanliness`.
console.log(myCarsCleanliness); // logs "You've washed your car." 
```

### FUNCTIONS
#### Defining (in global or current scope)
```javascript
function myFunction() {
  // ... your logic here between the braces {}
}
```

#### Defining (as a variable)
```javascript
var myFunction = function() {
  // ... your logic here between the braces {}  
}
```

#### Executing
```javascript
myFunction();
```

#### Defining (multiple arguments)
```javascript
function myFunction(someString, someBoolean, someNumber) {
  // ... your logic here between the braces {}    
}
```

#### Executing (multiple arguments)
```javscript
myFunction('a string', true, 1337); 
```

### CONDITIONALS
#### `if` conditional
```javascript
var iLikePizza = true; // store a boolean value
if (iLikePizza) {
  // ... your logic to perform if you like pizza between the braces {}
}
```

#### `if`/`else` conditional
```javascript
var iLikeBurgers = true; // store a boolean value
if (iLikeBurgers) {
  // ... your logic to perform if you like burgers between the braces {}
} else {
  // ... your logic to perform if you don't like burgers between the braces {}
}
```

#### `if`/`else if`/`else` conditional
```javascript
var steakPreference = prompt('How do you like your steak?'); // store a string value from user input

if (steakPreference === 'rare') { // NOTE the triple equal, this indicates a comparison instead of an assignment
  // ... your logic to perform if you prefer rare steak between the braces {}
} else if (steakPreference === 'medium rare') {
  // ... your logic to perform if you prefer medium rare steak between the braces {}
} else {
  // ... your logic to perform if you prefer steak any other way between the braces {}
}
```
#### `if` (multiple conditions)
```javascript
// variables from above
var age = 40;
if (age > 18 && age < 21) {
  console.log('you can smoke but you can\'t drink');
} else if (age < 18) {
   console.log('stay healthy youngin');
} else {
  console.log('PARTYYYYYYY'); // we're 40, we party... hard.
}
```

#### `if`/`else` (nested)
```javascript
var isSitting = confirm('Are you sitting?'); // store a boolean value from user input

if (isSitting) { // NOTE the triple equal, this indicates a comparison instead of an assignment
  var lastStoodUp = prompt('How many minutes has it been since you stood up?');
  if (lastStoodUp > 8) {
    // ... your logic to perform if user stood up 8+ minutes ago sitting between the braces {}
    alert('You should stand up!');
  } else {
    // ... your logic to perform if user stood up less than or equal to 8 minutes ago sitting between the braces {}
  }  
} else {
  // ... your logic to perform if user isn't sitting between the braces {}
}
```

## DOM Manipulation
#### Retrieving an element (by id)
```html
<header id="my-header">
  <h1 id="my-title"></h1>
</header>
```
```javascript
var myTitleElement = document.getElementById('my-title'); // stores the element above in a JavaScript variable
```

#### Retrieving an element (by selector (similar to style selectors))
```html
<div class="green"></div>
<div class="green bold"></div>
<div class="green"></div>
```
```javascript
var myGreenAndBoldDiv = document.querySelector('.green.bold'); // stores the second element above in a JavaScript variable
```

#### Setting an element's inner content
```javascript
myTitleElement.textContent = 'My Portfolio'; // sets the text of the `<h1>` above
// this populates the h1 and results in this on your page:
// <header><h1>My Portfolio</h1></header>
```

#### Setting an element's inner content (which includes some HTML)
```javascript
myTitleElement.innerHTML = '<a href="/portfolio.html">My Portfolio</a>'; 
// this populates the h1 with HTML and results in this on your page:
// <header><h1><a href="/portfolio.html">My Portfolio</a></h1></header>
```

#### Creating and manipulating a new element
```javascript
mySubtitleElement = document.createElement('h2'); // stores a new h2 in a JavaScript variable
mySubtitleElement.textContent = 'My portfolio is the best!'; // sets the inner text of the stored variable
```

#### Appending new element the page (using `appendChild()`)
```javascript
var myHeader = document.getElementById('my-header'); // store where we want to put our new element
myHeader.appendChild(mySubtitleElement); // append the previously created h2 to the `<header>` element
// this appends the h2 and results in this on your page:
// <header><h1>My Portfolio</h1><h2>My portfolio is the best!</h2></header> 
```

### DOM Events

#### Keyboard Press
```javascript
document.onkeyup = function(e) {
  console.log(e.key); // logs the user's key input when they release the key
};
```

## Other Helpful Items

#### Combining strings (using `+`)
```javascript
var age = 40;
var hello = 'Hello, I am Chris, I am NOT ' + age + '... yet'; 
// above line concatinates our string and age variable and stores them in a new variable
console.log(hello); // logs "Hello, I am Chris, I am NOT 40... yet"
```

#### Combining strings (using backticks aka template literals)
```javascript
var age = 40;
var hello = `Hello, I am Chris, I am NOT ${age}... yet`; 
// above line concatinates our string and age variable and stores them in a new variable
console.log(hello); // logs "Hello, I am Chris, I am NOT 40... yet"
```

#### Random Number (one of a few methods)
```javascript
var myRandomNumber = Math.floor(Math.random() * 10) + 1; // stores a random number between 1 and 10 in a variable named `myRandomNumber
```

#### Case Changing
```javascript
var leetString = 'SooO LeEt';
var quietString = leetString.toLowerCase();
var loudString = leetString.toUpperCase();
console.log(quietString, loudString); // logs "sooo leet" and "SOOO LEET"
```

#### First Character
```javascript
var hello = 'hello';
console.log(hello.charAt(0)); // logs "h"
```
