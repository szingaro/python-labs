# Lab 2

## Overview

Welcome to your first (or perhaps second) lab! Labs are designed to be your opportunity to experiment with Python and gain hands-on experience with the language.

The primary goal of the first half is to ensure that your Python installation process went smoothly, and that there are no lingering Python installation bugs floating around.

The second half focuses more on using data structures to solve some interesting problems.

You're welcome to work in groups or individually.

**Note: These labs are *designed* to be long! You shouldn't be able to finish all the problems in one class period. Work through as much as you can in the time allotted, but also feel free to skip from question to question freely. The extra problems are intended to be extra practice, if you want to hone your Python skills even more.**

Above all, have fun playing with Python! Enjoy.

### Running this notebook

To run a Jupyter notebook, first change directories (`cd`) to wherever you've downloaded the notebook. Then, from a command line run:

```bash
$ jupyter lab
```

You might need to `pip install jupyterlab` from within if you haven't yet. 

## Zen of Python

Run the following code cell by selecting the cell and pressing Shift+Enter.


```python
import this
```

    The Zen of Python, by Tim Peters
    
    Beautiful is better than ugly.
    Explicit is better than implicit.
    Simple is better than complex.
    Complex is better than complicated.
    Flat is better than nested.
    Sparse is better than dense.
    Readability counts.
    Special cases aren't special enough to break the rules.
    Although practicality beats purity.
    Errors should never pass silently.
    Unless explicitly silenced.
    In the face of ambiguity, refuse the temptation to guess.
    There should be one-- and preferably only one --obvious way to do it.
    Although that way may not be obvious at first unless you're Dutch.
    Now is better than never.
    Although never is often better than *right* now.
    If the implementation is hard to explain, it's a bad idea.
    If the implementation is easy to explain, it may be a good idea.
    Namespaces are one honking great idea -- let's do more of those!


## Hello World

Edit the following cell so that it prints `"Hello, world!"` when executed, and then run the cell to confirm.


```python
print("Hello, world!")
```

    Hello, world!


## Warming Up

### Fizz, Buzz, FizzBuzz!
If we list all of the natural numbers under 41 that are a multiple of 3 or 5, we get

```
 3,  5,  6,  9, 10, 12, 15,
18, 20, 21, 24, 25, 27, 30,
33, 35, 36, 39, 40
```

The sum of these numbers is 408.

Find the sum of all the multiples of 3 or 5 below 1001. As a sanity check, the last two digits of the sum should be `68`.

def fizzbuzz(n):
    """Returns the sum of all numbers less than n divisible by 3 or 5."""
    total_sum = 0
    for i in range(1,n):
        remainder_3 = i % 3
        remainder_5 = i % 5
        if remainder_3 == 0 or remainder_5 == 0:
            total_sum += i
        
    return total_sum

print(fizzbuzz(41))  # => 408
print(fizzbuzz(1001))

### Collatz Sequence
Depending on from whom you took math class, you may have seen this problem before.

The *Collatz sequence* is an iterative sequence defined on the positive integers by:

```
n -> n / 2    if n is even
n -> 3n + 1   if n is odd
```

For example, using the rule above and starting with 13 yields the sequence:

```
13 -> 40 -> 20 -> 10 -> 5 -> 16 -> 8 -> 4 -> 2 -> 1
```

It can be seen that this sequence (starting at 13 and finishing at 1) contains 10 terms. Although unproven, it it hypothesized that all starting numbers finish at 1.

What is the length of the longest chain which has a starting number under 1000?

*NOTE: Once the chain starts the terms are allowed to go above one thousand.*

Challenge: Same question, but for any starting number under 1,000,000. What about for any starting number under 10,000,000? You may need to implement a cleverer-than-naive algorithm.


```python
def collatz_len(n):
    """Computes the length of the Collatz sequence starting at n."""
    t = (n,)
    while n != 1:
        if n % 2 == 0:
            next_n = n / 2        
        else:
            next_n = (3 * n) + 1
        n = next_n
        t = t + (next_n,)
    
    print(t)
    return len(t)

def max_collatz_len(n):
    """Computes the longest Collatz sequence length for starting numbers less than n"""
    pass

print(collatz_len(13))  # => 10
print(max_collatz_len(1000))

# Challenge: Only attempt to solve these if you feel very comfortable with this material.
print(max_collatz_len(1000000))
print(max_collatz_len(100000000))

```

    (13, 40, 20.0, 10.0, 5.0, 16.0, 8.0, 4.0, 2.0, 1.0)
    10
    None


### Fahrenheit-to-Celsius converter
Write a program to convert degrees Fahrenheit to degrees Celcius by (1) asking the user for a number (not necessarily integral) representing the current temperature in degrees Fahrenheit, (2) converting that value into the equivalent degrees Celsius, and (3) printing the final equivalent value.

For example, your program should be able to emulate the following sample run:

```
Temperature F? 212
It is 100.0 degrees Celsius.

Temperature F? 98.6
It is 37.0 degrees Celsius.

Temperature F? 10
It is -12.222222222222221 degrees Celsius.
```

Want to be fancy (challenge)? Try to print the final temperature to two decimal places. For example, in the last case above we would print `-12.22` instead of `-12.222222222222221`. *Hint: Take a look at the [`round()`](https://docs.python.org/3/library/functions.html#round) function. Isn't Python great?*


```python
def convert_fahr_to_cels(deg_fahr):
    """Convert a temperature given in degrees Fahrenheit to degrees Celcius."""
    pass

def convert():
    """Ask the user for a temperature in degrees Fahrenheir, and print out the temperature in degrees Celsius."""
    pass
```

## Bonus Challenges

Don't worry about doing these bonus problems. In most cases, bonus questions ask you to think more critically or use more advanced algorithms.

In this case, we'll investigate advanced forms of printing and then reflect on Pythonic design.

### Zen Printing

Write a program using `print()` that, when run, prints out a tic-tac-toe board.

```
 X | . | . 
-----------
 . | O | . 
-----------
 . | O | X 
```

You may find the optional arguments to `print()` useful, which you can read about [here](https://docs.python.org/3/library/functions.html#print). In no more than five minutes, try to use these optional arguments to print out this particular tic-tac-toe board.


```python
# Print a tic-tac-toe board using optional arguments.
def print_tictactoe():
    """Print out a specific partially-filled tic-tac-toe board."""
    pass
```

Maybe you were able to print out the tic-tac-toe board. Maybe not. In the five minutes you've been working on that, I've gotten bored with normal tic-tac-toe (too many ties!) so now, I want to play SUPER tic-tac-toe.

Write a program that prints out a SUPER tic-tac-toe board.

```
  |  |  H  |  |  H  |  |  
--+--+--H--+--+--H--+--+--
  |  |  H  |  |  H  |  |  
--+--+--H--+--+--H--+--+--
  |  |  H  |  |  H  |  |  
========+========+========
  |  |  H  |  |  H  |  |  
--+--+--H--+--+--H--+--+--
  |  |  H  |  |  H  |  |  
--+--+--H--+--+--H--+--+--
  |  |  H  |  |  H  |  |  
========+========+========
  |  |  H  |  |  H  |  |  
--+--+--H--+--+--H--+--+--
  |  |  H  |  |  H  |  |  
--+--+--H--+--+--H--+--+--
  |  |  H  |  |  H  |  |  
```

You'll find that there might be many ways to solve this problem. Which do you think is the most 'pythonic?' Talk to someone next to you about your approach to this problem. Remember the Zen of Python!


```python
def print_super_tictactoe():
    """Print an empty SUPER tic-tac-toe board."""
    pass
```

## Investigating Data Structures

*[Optional Reading on Standard Types - check out Sequence types and Mapping types](https://docs.python.org/3/library/stdtypes.html)*

### Lists
Predict what the following lines of Python will do. Then, run the code block below to see if they match what you expect:

```Python
s = [0] * 3
print(s)
s[0] += 1
print(s)

s = [''] * 3
print(s)
s[0] += 'a'
print(s)

s = [[]] * 3
print(s)
s[0] += [1]
print(s)
```


```python
# Explore the elements of lists. Is the output what you expect?
s = [0] * 3
print(s)
s[0] += 1
print(s)

s = [''] * 3
print(s)
s[0] += 'a'
print(s)

s = [[]] * 3
print(s)
s[0] += [1]
print(s)
```

Why is this happening? Consider using the `id` function to investigate further. What happens when we replace the second-to-last line with `s[0] = s[0] + [1]`? What if we replace the line with `s[0].append(1)`?

### Tuples

Write a function to compute the [GCD](https://en.wikipedia.org/wiki/Greatest_common_divisor) of two positive integers. You can freely use the fact that `gcd(a, b)` is mathematically equal to `gcd(b, a % b)`, and that `gcd(a, 0) == a`.

You can assume that `a >= b` if you'd like.

It is possible to accomplish this in three lines of Python code (or with extra cleverness, even fewer!). Consider exploiting tuple packing and unpacking!

*Note: The standard library has a `gcd` function. Avoid simply importing that function and using it here - the goal is to practice with tuple packing and unpacking!*


```python
def gcd(a, b):
    """Compute the GCD of two positive integers."""
    pass  # Your implementation here
    
gcd(10, 25) # => 5
gcd(14, 15) # => 1
gcd(3, 9) # => 3
gcd(1, 1) # => 1
```

### Dictionaries (advanced)
In class, we saw a (naive) implementation of a dictionary comprehension that swaps the keys and values in a dictionary:

```
{value: key for key, value in dictionary.items()}
```

However, this approach will fail when there are two keys in the dictionary with the same value. Why will it fail?

Write a function that properly reverses the keys and values of a dictionary - each key (originally a value) should map to a collection of values (originally keys) that mapped to it. For example,

```
flip_dict({"CA": "US", "NY": "US", "ON": "CA"})
# => {"US": ["CA", "NY"], "CA": ["ON"]}
```

Note: there is a data structure in the `collections` module from the standard library called `defaultdict` which provides exactly this sort of functionality. You provide it a factory method for creating default values in the dictionary (in this case, a list.) You can read more about `defaultdict` and other `collections` data structures [here](https://docs.python.org/3/library/collections.html).


```python
def flip_dict(input_dict):
    """Reverse the keys and values of a dictionary."""
    pass
```

### Comprehensions (advanced)

#### Read

Predict the output of each of the following list comprehensions. After you have written down your hypothesis, run the code cell to see if you were correct. If you were incorrect, discuss with a partner why Python returns what it does.

```Python
[x for x in [1, 2, 3, 4]]
[n - 2 for n in range(10)]
[k % 10 for k in range(41) if k % 3 == 0]
[s.lower() for s in ['PythOn', 'iS', 'cOoL'] if s[0] < s[-1]]

# Something is fishy here. Can you spot it?
arr = [[3,2,1], ['a','b','c'], [('do',), ['re'], 'mi']]
print([el.append(el[0] * 4) for el in arr])  # What is printed?
print(arr)  # What is the content of `arr` at this point?

[letter for letter in "pYthON" if letter.isupper()]
{len(w) for w in ["its", "the", "remix", "to", "ignition"]}
```


```python
# Predict the output of the following comprehensions. Does the output match what you expect?
print([x for x in [1, 2, 3, 4]])
print([n - 2 for n in range(10)])
print([k % 10 for k in range(41) if k % 3 == 0])
print([s.lower() for s in ['PythOn', 'iS', 'cOoL'] if s[0] < s[-1]])

# Something is fishy here. Can you spot it?
arr = [[3,2,1], ['a','b','c'], [('do',), ['re'], 'mi']]
print([el.append(el[0] * 4) for el in arr])  # What is printed?
print(arr)  # What is the content of `arr` at this point?

print([letter for letter in "pYthON" if letter.isupper()])
print({len(w) for w in ["its", "the", "remix", "to", "ignition"]})
```

#### Write

Write comprehensions to transform the input data structure into the output data structure:

```
[0, 1, 2, 3] -> [1, 3, 5, 7]  # Double and add one
['apple', 'orange', 'pear'] -> ['A', 'O', 'P']  # Capitalize first letter
['apple', 'orange', 'pear'] -> ['apple', 'pear']  # Contains a 'p'

["TA_sam", "student_poohbear", "TA_guido", "student_htiek"] -> ["sam", "guido"]
['apple', 'orange', 'pear'] -> [('apple', 5), ('orange', 6), ('pear', 4)]

['apple', 'orange', 'pear'] -> {'apple': 5, 'orange': 6, 'pear': 4}
```


```python
nums = [1, 3, 5, 7]
fruits = ['apple', 'orange', 'pear']
people = ["TA_sam", "student_poohbear", "TA_guido", "student_htiek"]

# Add your comprehensions here!
```

### Pascal's Triangle
Write a function that generates the next level of [Pascal's triangle](https://en.wikipedia.org/wiki/Pascal%27s_triangle) given a list that represents a row of Pascal’s triangle.

```
generate_pascal_row([1, 2, 1]) -> [1, 3, 3, 1]
generate_pascal_row([1, 4, 6, 4, 1]) -> [1, 5, 10, 10, 5, 1]
generate_pascal_row([]) -> [1]
```

As a reminder, each element in a row of Pascal's triangle is formed by summing the two elements in the previous row directly above (to the left and right) that elements. If there is only one element directly above, we only add that one. For example, the first 5 rows of Pascal's triangle look like:

```
    1
   1 1
  1 2 1
 1 3 3 1
1 4 6 4 1
```

You may find the `zip` function discussed briefly in lecture useful, along with some cleverness. Alternatively, you could solve this problem with `enumerate`. Avoid using a loop of the form `for i in len(range(row)):`.

*Hint: Check out the diagram below. How could you use this insight to help complete this problem?*

```
  0 1 3 3 1
+ 1 3 3 1 0
-----------
  1 4 6 4 1
``` 


```python
def generate_pascal_row(row):
    """Generate the next row of Pascal's triangle."""
    pass

generate_pascal_row([1, 2, 1])  # => [1, 3, 3, 1]
generate_pascal_row([1, 4, 6, 4, 1])  # => [1, 5, 10, 10, 5, 1]
generate_pascal_row([])  # => [1]
```

#### Pretty Printing Pascal (Optional)

Given a number `n`, print out the first `n` rows of Pascal's triangle, centering each line. You should use the `generate_pascal_row` function you  wrote previously. The Pascal's triangle with 1 row just contains the number `1`.

To center a string in Python, you can use the `.center(width)` method. For example:

```
"CS".center(10)  # => '   CS   '
```

You can even specify an optional `fillchar` to fill with characters other than spaces!

The hardest part of this problem is determining the width of the bottom row of the triangle. You'll need to generate all rows of the triangle and store them before you can print any of them.


```python
def print_pascal_triangle(n):
    """Print the first n rows of Pascal's triangle."""
    pass
```

## Special Words

For each of the following problems, we describe a criterion that makes a word (or phrase!) special, similarly to our "Efficient Words" from lecture.

If you are using macOS or Linux, you should have a dictionary file available at `/usr/share/dict/words`, a 2.5M text file containing over 200 thousand English words, one per line. However, if you are offline or windows user the file can be found at `https://stanfordpython.com/res/misc/words`, so you can download the dictionary from there.

What would be an appropriate data structure in which to store the English words?

Write the method `load_english` to load English words from this file. How many English words are there in this file?


```python
# If you downloaded words from the course website,
# change me to the path to the downloaded file.
DICTIONARY_FILE = '/usr/share/dict/words'

def load_english():
    """Load and return a collection of english words from a file."""
    pass

english = load_english()
print(len(english))
```

### Triad Phrases

Triad words are English words for which the two smaller strings you make by extracting alternating letters both form valid words.

For example:

![Triad Phrases](http://i.imgur.com/jGEXJWi.png)

Write a function to determine whether an entire phrase passed into a function is made of triad words. You can assume that all words are made of only alphabetic characters, and are separated by whitespace. We will consider the empty string to be an invalid English word.

```
is_triad_phrase("learned theorem") # => True
is_triad_phrase("studied theories") # => False
is_triad_phrase("wooded agrarians") # => True
is_triad_phrase("forrested farmers") # => False
is_triad_phrase("schooled oriole") # => True
is_triad_phrase("educated small bird") # => False
is_triad_phrase("a") # => False
is_triad_phrase("") # => False
```

Generate a list of all triad words. How many are there? We found 2770 distinct triad words (case-insensitive).


```python
def is_triad_word(word, english):
    """Return whether a word is a triad word."""
    pass
    
def is_triad_phrase(phrase, english):
    """Return whether a phrase is composed of only triad words."""
    pass
```

### Surpassing Phrases (challenge)

Surpassing words are English words for which the gap between each adjacent pair of letters strictly increases. These gaps are computed without "wrapping around" from Z to A.

For example:

![Surpassing Phrases](http://i.imgur.com/XKiCnUc.png)

Write a function to determine whether an entire phrase passed into a function is made of surpassing words. You can assume that all words are made of only alphabetic characters, and are separated by whitespace. We will consider the empty string and a 1-character string to be valid surpassing phrases.

```python
is_surpassing_phrase("superb subway") # => True
is_surpassing_phrase("excellent train") # => False
is_surpassing_phrase("porky hogs") # => True
is_surpassing_phrase("plump pigs") # => False
is_surpassing_phrase("turnip fields") # => True
is_surpassing_phrase("root vegetable lands") # => False
is_surpassing_phrase("a") # => True
is_surpassing_phrase("") # => True
```

We've provided a `character_gap` function that returns the gap between two characters. To understand how it works, you should first learn about the Python functions `ord` (one-character string to integer ordinal) and `chr` (integer ordinal to one-character string). For example:

```python
ord('a') # => 97
chr(97) # => 'a'
```

So, in order to find the gap between `G` and `E`, we compute `abs(ord('G') - ord('E'))`, where `abs` returns the absolute value of its argument.

Generate a list of all surpassing words. How many are there? We found 1931 distinct surpassing words.


```python
def character_gap(ch1, ch2):
    """Return the absolute gap between two characters."""
    return abs(ord(ch1) - ord(ch2))

def is_surpassing_word(word):
    """Return whether a word is surpassing."""
    pass

def is_surpassing_phrase(word):
    """Return whether a word is surpassing."""
```

### Cyclone Phrases (challenge)

Cyclone words are English words that have a sequence of characters in alphabetical order when following a cyclic pattern. 

For example:

![Cyclone Phrases](http://i.stack.imgur.com/4XBV3.png)

Write a function that to determine whether an entire phrase passed into a function is made of cyclone words. You can assume that all words are made of only alphabetic characters, and are separated by whitespace.

```
is_cyclone_phrase("adjourned") # => True
is_cyclone_phrase("settled") # => False
is_cyclone_phrase("all alone at noon") # => True
is_cyclone_phrase("by myself at twelve pm") # => False
is_cyclone_phrase("acb") # => True
is_cyclone_phrase("") # => True
```

Generate a list of all cyclone words. How many are there? As a sanity check, we found 769 distinct cyclone words.


```python
def is_cyclone_word(word):
    """Return whether a word is a cyclone word."""
    
def is_cyclone_phrase(word):
    """Return whether a phrase is composed only of cyclone words."""
```

### Other Phrases (challenge)

On Puzzling.StackExchange, the user [JLee](https://puzzling.stackexchange.com/users/463/jlee) has come up with a ton of interesting puzzles of this form ("I call words that follow a certain rule "adjective" words"). If you like puzzles, optionally read through [these JLee puzzles](https://puzzling.stackexchange.com/search?q=%22I+call+it%22+title%3A%22what+is%22+is%3Aquestion+user%3A463) or [these other puzzles inspired by JLee](https://puzzling.stackexchange.com/search?tab=votes&q=%22what%20is%20a%22%20word%20is%3aquestion).

### Triangle Words
The nth term of the sequence of triangle numbers is given by 1 + 2 + ... + n = n(n+1) / 2. For example, the first ten triangle numbers are: `1, 3, 6, 10, 15, 21, 28, 36, 45, 55, ...`

By converting each letter in a word to a number corresponding to its alphabetical position (`A=1`, `B=2`, etc) and adding these values we form a word value. For example, the word value for SKY is `19 + 11 + 25 = 55` and 55 is a triangle number. If the word value is a triangle number then we shall call the word a triangle word.

Generate a list of all triangle words. How many are there? As a sanity check, we found 16303 distinct triangle words.

*Hint: you can use `ord(ch)` to get the integer ASCII value of a character. You can also use a dictionary to accomplish this!*


```python
def is_triangle_word(word):
    """Return whether a word is a triangle word."""
    pass
```

## Bonus Problems

*Only attempt to solve these bonus problems if you've finished the rest of the lab. Bonus problems are intentionally much harder than the other lab problems.*

### Polygon Collision

Given two polygons in the form of lists of 2-tuples, determine whether the two polygons intersect.

Formally, a polygon is represented by a list of (x, y) tuples, where each (x, y) tuple is a vertex of the polygon. Edges are assumed to be between adjacent vertices in the list, and the last vertex is connected to the first. For example, the unit square would be represented by

```
square = [(0,0), (0,1), (1,1), (1,0)]
```

You can assume that the polygon described by the provided list of tuples is not self-intersecting, but do not assume that it is convex.

**Note: this is a *hard* problem. Quite hard.**


```python
def polygon_collision(poly1, poly2):
    pass

unit_square = [(0,0), (0,1), (1,1), (1,0)]
triangle = [(0,0), (0.5,2), (1,0)]

print(polygon_collision(unit_square, triangle))  # => True
```

## Done Early?

Skim [Python’s Style Guide](https://www.python.org/dev/peps/pep-0008/), keeping the Zen of Python in mind. Feel free to skip portions of the style guide that cover material we haven't yet touched on in this class, but it's always good to start with an overview of good style.

## Credits for this Lab

*Credit to Puzzling.SE (specifically [JLee](https://puzzling.stackexchange.com/users/463/jlee)), ProjectEuler and InterviewCake for several problem ideas*
*Standford @sredmond*
