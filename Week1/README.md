# Exercises for elite hackers

- Create a GitHub account if you don't have one
- Create a new repo called `oop2019`
- Commit and push your files to this directory
- Invite or send me the public link by email, discord, slack or a flying owl from Hogwarts

If an exercise feels impossible, continue to the next one. You can solve the exercises in any order but they do get a little bit more difficult towards the end.

## Exercise 0

Please submit this form by Friday:

<a href="https://forms.gle/TXp1bLkjoaUoxds18">C# Proficiency level</a>

## Exercise 1

Let's see if we still remember how to write code.

As you know, `Console.ReadLine()` returns a `string`. Write a static method called `ReadInt` that repeatedly asks the user for an **`int`** instead. Additionally the method should take a `string` as an argument and write it to the user before asking.

It should work like this:

```c#
static void Main(string[] args)
{
    int x = ReadInt("Type a number: ");
    int y = ReadInt("Type another number: ");

    Console.WriteLine();
    Console.WriteLine($"{x} + {y} = {x + y}");
}
```

---

<pre>
Type a number: <b>no</b>
That's not a number, try again
Type a number: <b>1000</b>
Type another number: <b>337</b>

1000 + 337 = 1337
</pre>


## Exercise 2

Armed with your new `ReadInt` method, write an application that asks for two years, then outputs out all years between them and mark every leap year with a star.

* The years must be between 0 and 9999
* The second year must be after the first year

---
<pre>

 -- Amazing Leap Year Calculator 2019 --

 First year: <b>-1</b>
 Year must be between 0 and 9999.
 
 First year: <b>1982</b>
 OK
 
 Second year: <b>50</b>
 Year must be between 1982 and 9999.
 
 Second year: <b>1988</b>
 OK
 
 1982
 1983 
 1984 *
 1985
 1986
 1987
 1988 *
</pre>

*Hint: the `DateTime` class has a method called `IsLeapYear` that takes an integer for year as argument and returns **`true`** or **`false`**.*


## Exercise 3

Write a static method called `IsPalindrome` that returns **`true`** or **`false`** depending on whether a string is a palindrome or not (a palindrome is a string that reads the same backwards as forwards). The `IsPalindrome` method should ignore spaces and uppercase / lowercase.

It should work like this:

```csharp
IsPalindrome("Abba"); // true
IsPalindrome("nurses run"); // true
IsPalindrome("palindrome"); // false
```


## Exercise 4

Let's write FizzBuzz! Like the previous exercise it has become something of a classic when doing code interviews, so better you do it now when your employment is not on the line. You should know the whole backstory by reading <a href="https://blog.codinghorror.com/why-cant-programmers-program/">this blog post</a> first (written by Jeff Atwood, founder of Stack Overflow).

This is FizzBuzz: "Write a program that prints the numbers from 1 to 100. But for multiples of three print "Fizz" instead of the number and for the multiples of five print "Buzz". For numbers which are multiples of both three and five print "FizzBuzz"."

---

<pre>
1
2
Fizz
4
Buzz
Fizz
7
8
Fizz
Buzz
11
Fizz
13
14
FizzBuzz
etc...
</pre>

*Hint: if you don't know how to get the reminder of division, you need to read up on the modulus operator first.*

## Exercise 5

As you probably know, in .NET you can generate a random number this way:

```c#
var random = new Random();
var number = random.Next(1, 11);   // min is inclusive, max is exclusive

Console.WriteLine($"Random number between 1 and 10: {number}");
```

We can use this to play the very simple High/Low game that you might have implemented before*.

Randomize a number between 1 - 99. Let the user guess which number it is. If they get it wrong, give them a hint.

---

<pre>
Guess a number: <b>10</b>
too low

Guess a number: <b>40</b>
too low

Guess a number: <b>50</b>
too high

Guess a number: <b>42</b>
that is correct
</pre>

*Yes this exercise is lame, but it's a setup for the exercise below which is more interesting.*

## Exercise 6

Update the High/Low game to have a computer opponent for the user to play against. The computer plays by the same rules as the user - it does not know the number, but it understand the hints. This means that if either player guesses the number to be '45', and the game says that the number is too high, the computer opponent knows that it has to be lower than 45.

---

<pre>
Human vs super advanced AI computer. FIGHT!

Human guess: <b>80</b>
too high

Computer guesses the number is 46
too high

Human guess: <b>20</b>
too low

Computer guesses the number is 37
too high

Human guess: <b>33</b>
33 is correct, human is the winner
</pre>


## Exercise 7

Create yourself some old school loading bars! <a href="https://youtu.be/zKcM9gk5qMA?t=10">This is the effect you're going to emulate</a> by repeatedly writing out horizontal bars in different colors on the screen.

Here are some methods you might need:

| This        | Will do
| ------------- |-------------|
| `Console.WindowHeight` | Returns the height of the console window
| `Console.WindowWidth` | Returns the width of the console window
| `Console.SetCursorPosition(0,0)` | Moves the cursor to the top left of the screen
| `Console.BackgroundColor = color` |  Sets the color that you're drawing with

To generate a random bright color you can typecast an integer between 8 and 15 to `ConsoleColor`.

```csharp
var random = new Random();
var color  = random.Next(8, 16);   // 16 is exclusive

Console.BackgroundColor = (ConsoleColor)color;
Console.Write(" ");   // draw a box in some random color
```

## Exercise 8

It's Christmas! Well, soon anyway. Let the user input a number and render a Christmas tree of that size (= number of lines). Don't forget to add "[ ]" to the bottom center so it looks pretty.

You can repeat a **`char`** to a string in C# using this syntax:

```csharp
var repeated = new string('x', 5);   // "xxxxx"
```

---

<pre>
Please input size of tree: <b>8</b>

         *
        ***
       *****
      *******
     *********
    ***********
   *************
  ***************
        [ ]
</pre>


## Exercise 9

**The Map** - part 1 / 4

In this exercise you're going to read a map from a file and calculate how much land there is on it.

<a href="https://raw.githubusercontent.com/henrikql/yh-oop19/master/Week1/map.txt">Download this file</a> and save it somewhere on your disk.

The map is very simple, "." represents water and "#" represents land. Write an application that can read the map data and tell how much land there is ( = counts how many # there is).

It should work something like this:

```c#
var data = ReadMap("map.txt");
var land = CalculateNumberOfLandTiles(data);

Console.WriteLine($"Number of land tiles in map: {land}");
```
---
<pre>
Number of land tiles in map: 55
</pre>

*If you want to future proof your code for "The Map" part 2, 3 and 4, you should convert the map to a multidimensional or jagged array of some sort.*

## Exercise 10

Binary invader alert! Download <a href="https://raw.githubusercontent.com/henrikql/yh-oop19/master/Week1/invader.cs">this file</a>, it contains a jagged array (an array of arrays with a fixed size). You can get the dimensions of a jagged array using this syntax:

```csharp
var height = invader.GetLength(0);
var width  = invader.GetLength(1);
```

Copy the array to your project, go through the data row by row and write out `**` for every 1, and two empty spaces for every 0. Done correctly, your application should output this creature to the screen:

---
<pre>
    **          **
      **      **
    **************
  ****  ******  ****
**********************
**  **************  **
**  **          **  **
      ****  ****
</pre>

*Extra bonus exercise for the gold star in the corner achievement: Use `Console.MoveBufferArea` to move the invader back and forth across the screen! Use `Thread.Sleep()` to slow it down.*


## Exercise 11

So I heard you liked calculators! Write a method called `CalculateString()` that takes a string with a formula and returns the result. 

* Assume the string is always properly formatted with a space between each token
* The string can only contain integers, +, -, * and /
* No operator precedence, you simply calculate from left to right

```csharp
var formula = "1 + 2 * 3";
var result  = CalculateString(formula);
Console.WriteLine("{formula} = {result}");

var formula = "4 - 50 * 3 + 200 + 18 / 4";
var result  = CalculateString(formula);
Console.WriteLine("{formula} = {result}");
```
---
<pre>
1 + 2 * 3 = 9
4 - 50 * 3 + 200 + 18 / 4 = 20
</pre>

*Hint: you can tokenize a string to an array with `.Split()`*


## Exercise 12

Let's write Tetris! Hmm, we might not have the time for that, so let's just do a tiny part for now: rotating a block in one direction. A Tetris block is a matrix of 4x4, 3x3 or 2x2 that can be rotated left or right. Write a `RotateLeft()` method that takes a matrix of any size as the argument and returns it rotated 90 degrees. 

It should work like this:

```csharp
var block = new byte[,] {
    { 0, 0, 0 },
    { 1, 1, 1 },    
    { 0, 1, 0 },
}

block = RotateLeft(block);
// block is now:
//  0 1 0
//  0 1 1
//  0 1 0

block = RotateLeft(block);
// block is now:
//  0 1 0
//  1 1 1
//  0 0 0
```

*Hint: you don't need to swap the bytes from one position to another, it's easier (and probably cleaner code) to create a new matrix of the same size and copy the bytes to it.*


## Exercise 13

Actually let's write some more Tetris code! In modern versions of Tetris, the falling pieces aren't generated by pure randomness, instead the game is using something that's called "the bag system":

* There are seven different pieces in Tetris, call them 1 to 7.
* A "bag" (an array or a list) contains one of each type.
* When a new piece is needed, the game picks one at random and removes it from the bag.
* When the bag has no pieces left, it's replaced by a new bag and the process starts over.

You're free to implement this in any way you want, but ultimately the game shouldn't have to care how the randomization algorithm is written. 

In pseudo-code, the game client should be able to use your method that generates a new piece like this:
```c#
int piece;

while( ! GameOver)
{
    if (NeedNewPiece)
    {
        // gets a piece from the bag, or whatever random algorithm this version of Tetris is using
        piece = GenerateNewPiece();   
        Console.WriteLine($"Got this piece: {piece}");
    }

    // ... game continues until GameOver ...
}

```
*Bonus exercise: There's a famous Japanese Tetris game that has an addition to the bag system. The first piece picked from the bag must be 1, 2, 3, or 4.*
