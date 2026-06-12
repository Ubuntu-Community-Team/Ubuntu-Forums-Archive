---
title: "Help with regular expressions"
date: 2011-11-14
forum: General Help
---

### Post by carranty on 2011-11-14
I'm trying to develop a better understanding of the command line by working my way through the book "The Linux Command Line" by Schotts, available to view here

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

I'm on the section dealing with regular expressions on page 262.  He uses as an example the regular expression that will "only match lines consisting of groups of one or more alphabetic characters separated by single spaces:"

```

^([[:alpha:]]+ ?)+$
```

As an example he uses the grep command

```
carranty@carranty-desktop ~ $ echo "This that" | grep -E '^([[:alpha:]]+ ?)+$'
This that
```

The problem I'm having is that the + command seems not to work.  I get the same result if I leave it out

```
carranty@carranty-desktop ~ $ echo "This that" | grep -E '^([[:alpha:]] ?)+$' 
This that
```

and say I want to only match lines consisting of one alphanumeric character followed by a space.  I would think 
```

^([[:alpha:]]? ?)+$
```
would do the job (I've replaced the + with a ?), but it doesn't

```
carranty@carranty-desktop ~ $ echo "This that" | grep -E '^([[:alpha:]]? ?)+$'
This that
```
it still returns the line even though it has more than one character before the space.

Weirdly, the third quantifier (the first ? in the original code) works because if I pass a line with more than one space
```

carranty@carranty-desktop ~ $ echo "This  that" | grep -E '^([[:alpha:]]+ ?)+$' 
carranty@carranty-desktop ~ $ 
```
It doesn't output the line.  Can someone please help me out and explain what I'm doing wrong.

---

### Post by carranty on 2011-11-14
Ok, the above post may be a little long so heres a more basic example.  Say I want to match any lines consisting of MORE than 1 character.  Shouldn't 

```
[[:alpha:]]*
```

do it??  Because it isn't working for me

```
carranty@carranty-desktop ~ $ echo "T" | grep -E '[[:alpha:]]*'
T
```

---

### Post by mutley89 on 2011-11-15
> 
The problem I'm having is that the + command seems not to work.  I get the same result if I leave it out
[FONT=monospace]
```

^([[:alpha:]] ?)+$

```[FONT=Verdana]This will match the beginning of the line, followed by a letter and an  optional space (because of the '?'), one or more times.  To match a line  containing only 1 letter followed by a space use:[/FONT]
  
```
^[[:alpha:]] $
```[FONT=Verdana]To match multiple letters each followed by a space (eg. 'a b d e ', note the trailing space) use: [/FONT]
  
[/FONT][FONT=monospace]```
^([[:alpha:]] )+$
```[FONT=Verdana]to remove the requirement for a trailing space use:
  [/FONT]
[/FONT][FONT=monospace]```
^([[:alpha:]] )+[[:alpha:]]$
```[/FONT]


> 
and say I want to only match lines consisting of one alphanumeric character followed by a space.  I would think     ```
^([[:alpha:]]? ?)+$
``` would do the job (I've replaced the + with a ?), but it doesn't
This will match th beginning of the line, an optional letter followed by  an optional  space, one or more times, and the end of a line.  It will  therefore match any combination of letters and spaces.

> 
Weirdly, the third quantifier (the first ? in the original code) works because if I pass a line with more than one space
      ```

     carranty@carranty-desktop ~ $ echo "This  that" | grep -E '^([[:alpha:]]+ ?)+$'  carranty@carranty-desktop ~ $ 

```It doesn't output the line.  Can someone please help me out and explain what I'm doing wrong.     
Again the expression inside the parens matches one or more letters followed by a single optional space.

The '?'  matches the preceding expression 0 or 1 times.  To match something exactly once, just use it on it's own.

> 
          Ok, the above post may be a little long so heres a more basic example.   Say I want to match any lines consisting of MORE than 1 character.   Shouldn't 
 
      ```

     [[:alpha:]]* 

``` do it??  Because it isn't working for me
This matches a letter zero or more times.  Grep will therefore print  everything because every possible line contains zero or more letters[FONT=monospace]
[/FONT]

---

### Post by carranty on 2011-11-15
Thanks a lot mutley!  That's really cleared things up for me, thanks for going through them step by step :).

---

