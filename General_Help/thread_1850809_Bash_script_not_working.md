---
title: "Bash script not working"
date: 2011-09-27
forum: General Help
---

### Post by diogoteix on 2011-09-27
I've got a strange problem with bash scripting in Ubuntu 10.04.
When I try to invoque directly a simple "hello world" bash script, I got a ": No such file or directory" message. The executable permissions of the script file have been correctly set:
```
dtproxy@DTPROXY:/var/www$ ls -l
-rwx------ 1 dtproxy  dtproxy   240 2011-09-27 12:20 cron_test.sh

```In order to have bash correctly execute the script, I have to invoque it through a bash command, but then it returns an error at almost every line.


Here is the example script (taken from [https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)).

```
#!/bin/bash

clear
read -p "Please enter your name  : " name
echo ""
read -p "Please enter your age  : " age
echo ""
read -p "Please enter your sex. Male/Female  : " sex
echo ""
echo "So you're a $age year old $sex called $name"
```Here is the output:
```
dtproxy@DTPROXY:/var/www$ bash ./cron_test.sh
: command not founde 2:
: command not founde 3: clear
Please enter your name  : Test
': not a valid identifieread: `name

Please enter your age  : 33
': not a valid identifieread: `age

Please enter your sex. Male/Female  : Male
': not a valid identifieread: `sex

So you're a  year old  called
```Any idea on what is happening??

Thanks for your help

---

### Post by matt_symes on 2011-09-27
Hi

Are you using Windows carriage return and line feed endings ?

Was this what you were getting ?

```
matthew@matthew-laptop:~$ ./bb.sh
bash: ./bb.sh: /bin/bash^M: bad interpreter: No such file or directory
matthew@matthew-laptop:~$ 

```Kind regards

---

### Post by diogoteix on 2011-09-27
When I try to execute the script directly I do indeed get the output you refer:

```
dtproxy@DTPROXY:/var/www$ ./cron_test.sh
-bash: ./cron_test.sh: /bin/bash^M: bad interpreter: No such file or directory

```

I don't know what you mean by "Windows carriage return" and "line feed endings".
I wrote the script using VI through a putty session. 
At the end of the line, I just press the "Return" key. Is there something I'm missing?

---

### Post by matt_symes on 2011-09-27
Hi

> I wrote the script using VI through a putty session. 

On a windows machine ?

When you press return on the keyboard windows will add a carriage return and a line feed to the end of the line. It is what windows uses to delimit the end of a line.

Linux, on the other hand, just uses a line feed.

I don't use putty, but it may be adding the carriage return and line feed as the new line delimiter as you are running it through windows. 

You need to remove the carriage returns. It may be possible to configure putty to remove the carriage return.

Kind regards

---

### Post by sisco311 on 2011-09-27
You can change the file format in vim:
```
:set ff=unix
:wq
```

In nano you can press Ctrl+o, then Alt+d to toggle between DOS and unix file formats.

---

### Post by diogoteix on 2011-09-27
Indeed, when I open the script file in another text editor, I can see <CR><LF> symbols on every line...
I'll try to get a way around it with putty or another tool.

Thanks a lot for your help!

---

### Post by diogoteix on 2011-09-27
> **sisco311 said:**
> You can change the file format in vim:
```
:set ff=unix
:wq
```

In nano you can press Ctrl+o, then Alt+d to toggle between DOS and unix file formats.
Yep!

It works !

Thanks a lot!

---

### Post by matt_symes on 2011-09-27
Hi

> **sisco311 said:**
> You can change the file format in vim:
```
:set ff=unix
:wq
```In nano you can press Ctrl+o, then Alt+d to toggle between DOS and unix file formats.

A nice tip. I will remember that one.

BTW: When did half of the old timers on here become forums staff ? Congrats to you all.

Kind regards

---

