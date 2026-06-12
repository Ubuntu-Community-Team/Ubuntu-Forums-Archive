---
title: "Scripting"
date: 2010-03-05
forum: General Help
---

### Post by dstudentx on 2010-03-05
Im trying to learn scripting with a make file
I can write a simple C++ program and have the make file compile it.

but how could I have the makfile ask the user for a directory then after the directory is taken in as an input from the user display the directory?  is this even possible?

---

### Post by flippo on 2010-03-05
Makefiles are not made for user input.  I would recommend python or bash for something like that (its pretty easy in both languages).

EDIT:
I should also note, I'm not actually sure if it IS possible to do something like that in a makefile, or how you would do it.

---

### Post by dstudentx on 2010-03-05
what about a simple script written in C++.  can I have the user prompted and input a file name and have the C++ program output the contents of the folder?

---

### Post by flippo on 2010-03-05
Yes, C++ is an extension of C and pretty much the entire linux kernel is written in C.  C++ is not a scripting language though, so I did not mention it.  Look at the dirent.h library for directories (yay man pages) and get input from standard in (iostreams in c++).

Good luck :) Enjoy hacking.

---

### Post by dstudentx on 2010-03-05
what about in a script

like
#!/bin/bash
# My first script

echo "Hello World!"



how could I do

echo "enter a folder to view"
how is input taken in and executed ?

---

### Post by flippo on 2010-03-05
Make a file newls:
```
#!/bin/bash
ls $1
```

run
```
chmod +x newls
```

run newls the first argument is $1 second $2...
```
./newls /home/
```

I don't remember how to get real time input off the top of my head...

---

### Post by dstudentx on 2010-03-05
Wow thank you soo. much your a stud. 

last question

say i want to person to enter

./newls --data

that the output would be the same as  
df 
of 
free

---

### Post by flippo on 2010-03-05
I don't understand what your asking.  Can you reword it?

---

### Post by dstudentx on 2010-03-05
sure.

prints out the list of files in the directory
```
./newls /home/
```how can i also output what this would ```
user:~$ free
``` if the user types this
```
./newls free
```

---

### Post by flippo on 2010-03-05
do you mean something like this?```
#!/bin/bash
if [ $1 == free ]; then
  free
else 
  ls $1  
fi
```

Here is a bash tutorial (I used it to recall the if notation)
[http://www.linuxconfig.org/Bash_scripting_Tutorial]("http://www.linuxconfig.org/Bash_scripting_Tutorial")

---

### Post by dstudentx on 2010-03-05
Dude you are so amazing!

what language does scripting use.  its looks like C++ but is it C

---

### Post by flippo on 2010-03-05
Scripts are a type of language.  There are different types and classifications of programming languages.  C and C++ are compiled languages.  You have to compile them after you write them.  This makes them faster, but more difficult to work with.  Other languages, like python and bash are interpreted, they are compiled as they run.  They often look similar to a C style language, but they are slightly different.  Since they are compiled as they run they are much slower (20x or so for some applications) but easier to use and have some nice perks.  If your doing something that doesn't need speed, or is IO bound, its usually best to use a scripting language to do it.

So in short, the scripts are in bash.  Bash is its own language :-P.  You'd be amazing how many languages there are, and how odd they can be, like [Shakespeare]("http://en.wikipedia.org/wiki/Shakespeare_(programming_language)")

---

### Post by dstudentx on 2010-03-06
this stuff is really interesting. I usually only think of the big ones (java, C++, Assembly<-really struggle with)



I'm sorry to ask again but I can;t seem to have two if statements
```
#!/bin/bash
if [ $1 == -d ]; then
 free
if [ $1 == --help ]; then
  help
else 
  ls $1  
fi
```

---

### Post by Agent ME on 2010-03-06
> **dstudentx said:**
> I'm sorry to ask again but I can;t seem to have two if statements
```
#!/bin/bash
if [ $1 == -d ]; then
 free
if [ $1 == --help ]; then
  help
else 
  ls $1  
fi
```

Your first if block needs to end with a "fi". Also, you should put the $1 terms in quotes so that spaces aren't lost:
```
#!/bin/bash
if [ "$1" == -d ]; then
 free
fi
if [ "$1" == --help ]; then
  help
else 
  ls "$1"
fi
```

---

### Post by asmoore82 on 2010-03-06
> **dstudentx said:**
> what about a simple script written in C++.  can I have the user prompted and input a file name and have the C++ program output the contents of the folder?

If you want to do some simple BASH scripting with a "wow" factor,
check out the zenity package...

```
#!/bin/bash

title="${0##*/}"

if zenity --info --title "Hello and Welcome" --text "Please select a folder to view a long listing of its contents."; then

   userinput="$( zenity --file-selection --directory --title "$title" )"

   if [ -d "$userinput" ]; then
      ls -lF "$userinput" | zenity --list --title "$title" --width 800 --height 600 --column "ls -lF" --text "$userinput"
   else
      zenity --warning --title "$title" --text "User canceled file selection\!"
   fi
else
   zenity --warning --title "$title" --text "User wouldn't even say \"OK\!\""
fi

#End of File
```

---

### Post by dstudentx on 2010-03-09
That's amazing.  How about writing a script without using tree but getting the same output as tree would produce

---

