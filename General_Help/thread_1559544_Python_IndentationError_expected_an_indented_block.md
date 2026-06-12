---
title: "Python: IndentationError: expected an indented block"
date: 2010-08-23
forum: General Help
---

### Post by cgroza on 2010-08-23
Hi, I am trying to do my first Python program and I am having a little bit of trouble. I get this "IndentationError: expected an indented block". I tried searching google for a solution and i found some but i could not implement them. I am trying this after reading a few tutorials and a book about python. I would appreciate if someone could indicate me how to fix the error.  Thank you.
Here is the code:
If you see any syntax errors please indicate them too me. As you can see I am a beginner.
```

#size_calculator.py
#!/usr/local/bin/python
import time
import datetime
today = datetime.date.today()
print "The date is", today 



print('This program calculates the perimeter, surface, and the volume.')
def     selection() :
 d = raw_input( 'Enter p to calculate the perimeter, enter v to calculate the volume, enter s to calculate the surface, or Ctrl+C to exit! p/v/s :')   


if d == 'p':
def perimeter():
 while 1:
  a= raw_input('Enter the lenght: ')
  b= raw_input('Enter the width: ')
  print('The perimeter is'),a+b
  selection
  if d == 'v' : volume()
  if d == 's' : surface()
  if d == 'p' : perimeter()
 print('The program will exit, thank you for using it.')
 raw_input('Press <enter> to exit')


if d == 'v':
def volume():
 while 2:
  g= input('Enter the height: ') 
  f= input('Enter the lenght: ')
  h= input('Enter the width: ')
  print('The volume is '),g*f*h
  selection
  if d == 'v' : volume()
  if d == 's' : surface()
  if d == 'p' : perimeter()
 print('The program will exit, thank you for using it.')
 raw_input('Press <enter> to exit')


if d == 's':
def surface():
 while 3:
  n= input('Enter the lenght: ')
  m= input('Enter the width: ')
  print('The surface is '),n*m
  selection
  if d == 'v' : volume()
  if d == 's' : surface()
  if d == 'p' : perimeter()
 print('The program will exit now, thank you for using it.')    
 raw_input('Press <enter> to exit')
```This is the error output from the terminal: 
```
cgroza@cgroza-desktop:~/Desktop$ python program.py 
  File "program.py", line 16
    def     perimeter():
      ^
IndentationError: expected an indented block
cgroza@cgroza-desktop:~/Desktop$ python program.py 
  File "program.py", line 16
    def     perimeter():
      ^
```

---

### Post by cgroza on 2010-08-23
bump

---

### Post by spjackson on 2010-08-23
[FONT=monospace]Welcome to python!

Essentially, the if statement ```
if d == 'p':
```requires an indented block to follow it which will be executed if the test condition is true. The next line after the if is
```
def perimeter():
```and this is not indented and it would need to be to go with the preceding if.

However, you would normally define your functions before the rest of the code. Having your function definitions within the scope of an if is unusual.

Using a single space for each level of indent is also unusual; 2, 3 or 4 spaces are more common. 

So, I suggest you move the 3 function definitions to come immediately
after the imports. Then you'd do
```

if d == 'p' :
    perimeter()
if d == 'v' :
    volume()
if d == 's' :
    surface()

```[/FONT]

---

### Post by cgroza on 2010-08-23
I got it figured by now. Thanks for your reply. My program works now and  i learned my lesson to always define the functions at the beginning of the program. I'm sure you will see me around with post like this for a while.

---

### Post by Surf Musician on 2010-08-25
Hi, I'm having a problem with the indentation in my python code as well and I need some help with it please!

I have several nested if, else, and elif statements, and I thought I had the indentation correct for what I'm trying to do. Here's some of the code:


if (five[i] == five[j] and i != j):
         >>#WE HAVE 5TH DIGIT MATCH
         >>if (six[i] == six[j] and i != j):
                 >>>>#WE HAVE EXACT MATCH
                 >>>>if (i < j):
                         >>>>>>sim[i] = sim[i] + 1
                         >>>>>>sim[j] = 0
                         >>>>>>discard[j] = 1
                 >>>>elif (j < i):
                         >>>>>>sim[j] = sim[j] + 1
                         >>>>>>sim[i] = 0
                         >>>>>>discard[i] = 1
         >>else:
                 >>>>#NOT COMPLETE MATCH
elif (five[i] == six[j] and i != j):
     >>#WE HAVE 5TH DIGIT MATCH
         >>if (six[i] == five[j] and i != j):
                 >>>>#WE HAVE EXACT MATCH
     >>else:
                 >>>>#NOT COMPLETE MATCH


I'm getting the same error: "IndentationError: expected an indented block" at the second elif statement, the one that's on the same indentation line as the first line. I don't want this elif indented, I want it to be an elif relating to the first if statement of the code. So if the first if evaluates to false, I want the test if the elif in question is true or false. Any help is greatly appreciated!!!
Thanks!

---

### Post by Vaphell on 2010-08-25
put that in [code] tags

your else in the middle doesn't have any followup (only comments) and then it jumps to elif of outer if. If at the end does the same thing. If you want to do an empty operation, use 'pass'. Comments are only for humans, they don't exist from program's perspective
I don't know what your algorithm is supposed to do but it looks overly convoluted. Is there any possibility to make it cleaner? Could you explain what you want to achieve?

---

### Post by Surf Musician on 2010-08-25
Sorry, I put in the comments as a place holder for some code I'm adding later. But I guess that's the problem here, I replaced all the comments with a dummy variable assignment and the issue went away. Thanks!

---

### Post by Vaphell on 2010-08-25
as i said 'pass' is designed to be a placeholder, no need to multiply variables to occupy space :)

---

### Post by Surf Musician on 2010-08-25
Oh good to know! thanks, I'm new to python. I've only done C/C++/Perl so far.

---

