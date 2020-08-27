# 8.1: Program Lifecycle and State

{% embed url="https://www.youtube.com/watch?v=oxxwcMJN8ec" caption="" %}

## Global World State

Without mentioning it, our programs have so far dealt with data that only exists while `main` runs or while any other function runs.

Now we will want to expand the kinds of data that our program deals with and can manipulate.

## Memory, Holding Values

We want to keep track **for the life of our program** what the bank roll is.

We need a syntax for a value \(bank roll\) that gets updated when `main` runs and then is **also** available the next time `main` runs.

We'll also define **life of our program** as the time from when it loads in the browser to the next time we close the tab or hit the refresh button \(load the page again\).

First let's prove the basic behavior that when we initialize a value in the console we can manipulate it and get the new value out:

```javascript
var number = 5;
```

```javascript
number = number * 2;
```

```javascript
number
```

If we refresh the page that value is no longer available. The life of our program has ended and started again.

### Main Function Scope

Remember that for a `main` function like this:

```javascript
var main = function (input) {
  var myOutputValue = kilometersToMiles(input);

  return myOutputValue;
};
```

`myOutputValue` is different and the value is only set for that one time when we click submit.

Note that when you try to check the value of `myOutputValue` in the console it doesn't exist.

```javascript
myOutputValue
```

This is a generic truth about values that are initialized inside a function. They are available for the life of that function, then they disappear.

Note that main function runs each time the submit button is clicked.

### Global State

{% embed url="https://www.youtube.com/watch?v=xVIAh\_o4mPc" caption="" %}

```javascript
var papayaCounter = 0;

var main = function (input) {
  var myOutputValue = 'You have ' + papayaCount + ' papayas';
  return myOutputValue;
};
```

## Dice Betting

{% embed url="https://youtu.be/X-b\_LJAJIsU" caption="" %}

Let's add betting on the dice roll.

```javascript
var bankRoll = 10;

var main = function (input) {
  var randomDiceNumber = diceRoll();

  var myOutputValue = 'you lose. current bank roll: ' + bankRoll;

  if (randomDiceNumber == input) {
    bankRoll = bankRoll + 1;

    myOutputValue = 'you win. current bank roll: ' + bankRoll;
  }

  return myOutputValue;
};
```

## Exercises

{% hint style="info" %}
**1\) Follow along with the video and duplicate the code.**

**2\) Apps**

Put this basic dice game into the starter code:

```javascript
var diceRoll = function () {
  // produces a decimal between 0 and 6
  var randomDecimal = Math.random() * 6;

  // take off the decimal
  var randomInteger = Math.floor(randomDecimal);

  // it's anumber from 0 - 5 ... add 1
  var diceNumber = randomInteger + 1;

  return diceNumber;
};

var main = function (input) {
  var randomDiceNumber = diceRoll();

  var myOutputValue = 'you lose';

  if (randomDiceNumber == input) {
    myOutputValue = 'you win';
  }

  return myOutputValue;
};
```

**Last Roll**  
Create a version of the dice game that tells the user what their previous dice roll was.

Example:

```text
Your last roll was 4. You just rolled a 3. You guessed 3. You win!
```

**Win / Loss**  
As the user continues to play the game, tell them what their current win / loss percentage is.

Example:

```text
You win 23.5% of the time. You just rolled a 4. You guessed 3. You lose!
```

#### More Comfortable

**Most Rolled**

Keep track of the number that's rolled the most times.

Example:

```text
You just rolled a 4. 2 is the number you roll the most. You guessed 3. You lose!
```

**Betting**  
If the user guess is off by 1 they win 1. If it's exact they win 2.

**Advanced Betting**  
The user can be off up to 4. They win 1 if they are off by 4 and win 4 if they guess exactly.
{% endhint %}
