---
title: "Whats these 2  Linux Commands?"
date: 2011-07-18
forum: General Help
---

### Post by PossumNZ on 2011-07-18
dpkg -l | grep unity 

I can read all the letters  in this command line except the two letters between  the 2 gs.

Are they a  letter, a space, a number? 

This stuff easy when you know how!

---

### Post by terrykiwi83 on 2011-07-18
it is a -'minus symbol' with a small case L following. Then a space and a straight line which is usually above the enter key (NZ) (have to hold shift to activate it).

-l |

or just copy and paste the command

---

### Post by nothingspecial on 2011-07-18
> **PossumNZ said:**
> dpkg -l | grep unity 

I can read all the letters  in this command line except the two letters between  the 2 gs.

Are they a  letter, a space, a number? 

This stuff easy when you know how!

-l is a argument to the dpkg command
```

              -l, --list package-name-pattern...
                  List packages matching given pattern.
```


| is a pipe, which sends the output of the command on the left to the input of the one on the right

---

### Post by Hostie on 2011-07-18
> **PossumNZ said:**
> dpkg -l | grep unity 

I can read all the letters  in this command line except the two letters between  the 2 gs.

Are they a  letter, a space, a number? 

This stuff easy when you know how!

What is happening here is you are running two commands.

1) you are running dpkg is the package manager ( to install programs) and you are running it with the option of l (lowercase L) which lists the packages.

2) you are running grep which is used for searching, more specifically for the word unity

the vertical line between the two commands takes the output from command 1 and feeds it as input to command 2.  (shift plus forward slash) 

So to put it together, you are searching the list of all packages for ones named unity.  Hope  this helps!

---

