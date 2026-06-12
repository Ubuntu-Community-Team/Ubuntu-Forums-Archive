---
title: "Help with python"
date: 2011-04-17
forum: General Help
---

### Post by bance on 2011-04-17
Hi all,

I've decided to try to learn python, I'm working through [_[COLOR=Red]this[/COLOR]_]("http://openbookproject.net/thinkcs/python/english2e/ch05.html") tutorial, and I've got myself stuck.

I'm at the section 5.8 "Unit testing" 

here is my code :-

```
#!/usr/bin/python

def is_divisible_by_2_or_5(n):
    """
      >>> is_divisible_2_or_5(8)
      True
      >>> is_divisible_2_or_5(7)
      False
      >>> is_divisible_2_or_5(5)
      True
      >>> is_divisible_2_or_5(9)
      False
    """
    return n % 2 == 0 or n % 5 == 0

is_divisible_by_2_or_5(8)

if __name__ == '__main__':
    import doctest
    doctest.testmod()

```The code is exactly as the tutorial, except I've added a call, but whether the call is there or not, the code does not pass the doc test, and I believe it should!

This is what I get when I run the code in a bash shell :-

```
stephen@stephen-desktop:~/bin$ myfunctions.py 
**********************************************************************
File "/home/stephen/bin/myfunctions.py", line 5, in __main__.is_divisible_by_2_or_5
Failed example:
    is_divisible_2_or_5(8)
Exception raised:
    Traceback (most recent call last):
      File "/usr/lib/python2.6/doctest.py", line 1248, in __run
        compileflags, 1) in test.globs
      File "<doctest __main__.is_divisible_by_2_or_5[0]>", line 1, in <module>
        is_divisible_2_or_5(8)
    NameError: name 'is_divisible_2_or_5' is not defined
**********************************************************************
File "/home/stephen/bin/myfunctions.py", line 7, in __main__.is_divisible_by_2_or_5
Failed example:
    is_divisible_2_or_5(7)
Exception raised:
    Traceback (most recent call last):
      File "/usr/lib/python2.6/doctest.py", line 1248, in __run
        compileflags, 1) in test.globs
      File "<doctest __main__.is_divisible_by_2_or_5[1]>", line 1, in <module>
        is_divisible_2_or_5(7)
    NameError: name 'is_divisible_2_or_5' is not defined
**********************************************************************
File "/home/stephen/bin/myfunctions.py", line 9, in __main__.is_divisible_by_2_or_5
Failed example:
    is_divisible_2_or_5(5)
Exception raised:
    Traceback (most recent call last):
      File "/usr/lib/python2.6/doctest.py", line 1248, in __run
        compileflags, 1) in test.globs
      File "<doctest __main__.is_divisible_by_2_or_5[2]>", line 1, in <module>
        is_divisible_2_or_5(5)
    NameError: name 'is_divisible_2_or_5' is not defined
**********************************************************************
File "/home/stephen/bin/myfunctions.py", line 11, in __main__.is_divisible_by_2_or_5
Failed example:
    is_divisible_2_or_5(9)
Exception raised:
    Traceback (most recent call last):
      File "/usr/lib/python2.6/doctest.py", line 1248, in __run
        compileflags, 1) in test.globs
      File "<doctest __main__.is_divisible_by_2_or_5[3]>", line 1, in <module>
        is_divisible_2_or_5(9)
    NameError: name 'is_divisible_2_or_5' is not defined
**********************************************************************
1 items had failures:
   4 of   4 in __main__.is_divisible_by_2_or_5
***Test Failed*** 4 failures.

```I'm sure I'm missing something simple, but I just can't see it !

Can anybody point me in the right direction?

TIA Steve

---

### Post by dracayr on 2011-04-17
put the doctest example session behind the definition of is_divisible_by_2_or_5 -- behind the return statement, that is.
Also, as it is, the program won't output anything -- not sure if you want it to

---

### Post by bance on 2011-04-17
Hi dracayr,

thanks for the reply.....

Gonna mark this as solved....   turns out it was a syntax error that was throwing me:-


[LIST]
[*]is_divisible_by_2_or_5
[*]is_divisible_2_or_5
[/LIST]
I suppose the lesson to learn here is to trust the errors thrown up! (NameError)

A fresh pair of eyes as they say.

---

