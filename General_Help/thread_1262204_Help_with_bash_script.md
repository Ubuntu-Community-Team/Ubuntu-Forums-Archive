---
title: "Help with bash script"
date: 2009-09-09
forum: General Help
---

### Post by Loetje on 2009-09-09
Hi,

Can anyone help me with making a bash script for the following.
I'm quite the beginner at this and i can't get it done

I want to cp -r {folder} to {destination1} and then mv {folder} to destination 2 where {folder} has to be a variable. Also, the folder has to be recognized by autocomplete using tab.

---

### Post by NoaHall on 2009-09-09
```
#!/bin/bash
       echo Please select folder:
read FOLDER
cp -r $FOLDER {destination1} &&
mv $FOLDER {destination2}

```
done

---

### Post by epicoder on 2009-09-09
'done' is supposed to be used to end a loop. The proper command is exit 0 for success and exit 1 for failure.

---

### Post by NoaHall on 2009-09-09
Yeah, sorry, the done wasn't part of the script.

Fixed to avoid confusion

---

### Post by The Cog on 2009-09-09
read doesn't do autocomplete. Try this:

```
#!/bin/bash

if [ _$1 == _ ] ; then
   echo -n 'What is the source directory? '
   read src
else 
    src=$1
fi
cp -r $src {destination1} && mv $src {destination2}
```
Then you can give the source directory on the command line as an argument, where ~ and Tab will work as expected.

---

### Post by Loetje on 2009-09-11
Thanks for all the great help. The first script works but without autocomplete, the script by The Cog works too but also autocomplete doesn't work. What am i doing wrong?
I get a prompt saying:
What is the source directory?
I the start typing the beginning of the name of the directory and press tab but other then the cursor jumping forward 1 tab nothing happens...

---

### Post by Loetje on 2009-09-11
Ok ok sorry, as an argument, i get it. Autocomplete works now, but i'm trying to do this with a directory that has spaces in it:

 my_script Downloads/DJ\ Whiteowl\ -\ Whiteowl\ Drop\ That\ 81/
./my_script: line 4: [: too many arguments
cp: cannot stat `Downloads/DJ': No such file or directory
cp: cannot stat `Whiteowl': No such file or directory
cp: cannot stat `-': No such file or directory
cp: cannot stat `Whiteowl': No such file or directory
cp: cannot stat `Drop': No such file or directory
cp: cannot stat `That': No such file or directory
cp: cannot stat `81/': No such file or directory

---

### Post by Loetje on 2009-09-11
by the way, it works perfectly for folder without spaces in the name!

---

### Post by DaithiF on 2009-09-11
replace $src with "$src" in the last line to get around the problem for filenames with spaces.

---

### Post by Loetje on 2009-09-16
OK, that works. I do get this output:

```
my_script Downloads/DJ\ Ill\ Will\ \&\ DJ\ Rockstar\ Present\ Bow\ Wow\ -\ Greenlight-2009-MIXFIEND/
./my_script: line 4: [: too many arguments
```

the code is now:

```
#!/bin/bash

if [ _$1 == _ ] ; then
   echo -n 'What is the source directory? '
   read src
else 
    src=$1
fi
cp -r "$src" ~/2iaudio && mv "$src" ~/Music@1T

```
But the folder is still moved and copied.

---

### Post by DaithiF on 2009-09-16
try:
```
#!/bin/bash

if [[COLOR=Red] "$1" == "" [/COLOR]] ; then
   echo -n 'What is the source directory? '
   read src
else 
    src=$1
fi
cp -r "$src" ~/2iaudio && mv "$src" ~/Music@1T

```

the error message tells you the problem: 
[: too many arguments
because you don't enclose $1 in quotes, it seems to [ (the program that performs comparisons), that you are passing it MANY things to compare ... like saying if [ thing1 thing2 thing3 thing4 == something ] rather than if [ "thing with spaces in its name" == something ]

---

### Post by Loetje on 2009-10-13
That's the solution! Thanks. Btw, I could have never done this on my own. Where can i learn more about shell programming?

---

### Post by DaithiF on 2009-10-13
i would just start by googling shell programming ... you'll find hundreds of guides, how-tos, tutorials.

---

### Post by ibuclaw on 2009-10-13
> **DaithiF said:**
> try:
```
#!/bin/bash

if [[COLOR=Red] "$1" == "" [/COLOR]] ;

```

```
if [ "$1" = "" ]; then
```
Will work in the exact same way too ;)

What most scripters tend to do though, is this:
```
if [ x$1 = x ]; then
```
Your choice really though.

Regards
Iain

---

### Post by DaithiF on 2009-10-13
> 
What most scripters tend to do though, is this:
```
if [ x$1 = x ]; then
```Your choice really though.


aarrgh, that was the whole point of the post though (if you read from the top) ... the OP was doing more or less exactly that [ _$1 == _x ], and it was failing because of spaces in his $1 variable.  hence the quotes...

---

### Post by ibuclaw on 2009-10-14
> **DaithiF said:**
> aarrgh, that was the whole point of the post though (if you read from the top) ... the OP was doing more or less exactly that [ _$1 == _x ], and it was failing because of spaces in his $1 variable.  hence the quotes...

Ah, spaces in filenames are a bad habit, that. ;)

Stil only requires 2 extra characters though.
```
if [ "x$1" = x ]; then
```

---

