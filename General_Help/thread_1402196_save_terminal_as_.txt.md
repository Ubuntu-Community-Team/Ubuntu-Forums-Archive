---
title: "save terminal as .txt"
date: 2010-02-08
forum: General Help
---

### Post by metalf8801 on 2010-02-08
In OS X the terminal has the option to save session as which saves the terminal season as a .txt file I'm looking for away to do this on Ubuntu.  I know I can just copy and past but I was hoping for another option

---

### Post by jamesisin on 2010-02-08
You can set up your terminal to capture all input/output to a file:

```
script [nameofsomefilehere]
```

For more information see:

```
man script
```

Basically, everything you enter/type and everything the shell prints to the screen will be copied to a text file as you go along.

---

### Post by golanbatrac on 2010-02-08
To write the stdout and stderr of individual commands to a text file, use tee: 

```
<command> 2>&1 | tee file.txt
```

---

### Post by metalf8801 on 2010-02-09
Thank you I will try both of those but if anyone else has any ideas I would love to hear them 

Thank you 
Dan

---

### Post by mushwars on 2010-02-09
they have two powerful options but there are really easy ones that EVERYONE should know.


output redirection

command **>** file <-- this will make a file called file with the output of command.
command **>>** file <-- this will append file with the output of command.

if the file is garbled add 2>&1


EDIT: also a program called wgetpaste you will have to build it from source, but it allows you to output redirct to dpaste (a pastebin).
```
dmesg | wgetpaste
```
result: your code is at : [http://wgetpaste.com/XXXXXX](http://wgetpaste.com/XXXXXX)

---

