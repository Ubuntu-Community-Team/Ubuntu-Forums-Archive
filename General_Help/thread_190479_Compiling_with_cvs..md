---
title: "Compiling with cvs."
date: 2006-06-06
forum: General Help
---

### Post by tdrusk on 2006-06-06
Okay I really really want DC++ and on their page they talk about checking out the cvs and downloading it and installing it.

> To check out the CVS anonymously:
cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login
(leave password blank)
cvs -z3 -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp co linuxdcpp 


ok first thing...
If I put each one of those in with sudo behind it it asks me for a password, i hit enter and thats all that it does. In the guide on this page it says that it puts a linuxdcpp folder in your home folder. I am not getting that. Any clue on what I'm doing wrong?

---

### Post by Kilz on 2006-06-06
[QUOTE=fuzzyhair]Okay I really really want DC++ and on their page they talk about checking out the cvs and downloading it and installing it.



ok first thing...
If I put each one of those in with sudo behind it it asks me for a password, i hit enter and thats all that it does. In the guide on this page it says that it puts a linuxdcpp folder in your home folder. I am not getting that. Any clue on what I'm doing wrong?[/QUOTE]


I just compiled this program last night. Its very nice even though its descriped as alpha software. Just use the line below.

```
cvs -z3 -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp co linuxdcpp 
```

It will download the cvs source to a linuxdcpp folder in your home folder. The Readme.txt in that folder has good compile instructions.

---

### Post by tdrusk on 2006-06-06
> bash: cvs: command not found

eek. I put sudo before it and it asked me for a password and i hit enter.
I dont see that folder :(

---

### Post by Kilz on 2006-06-06
[QUOTE=fuzzyhair]eek. I put sudo before it and it asked me for a password and i hit enter.
I dont see that folder :([/QUOTE]

Dont put sudo before it.

---

### Post by tdrusk on 2006-06-06
[QUOTE=Kilz]Dont put sudo before it.[/QUOTE]
I have no idea what I did differently but it worked. I am compiling it now. Thanks.

---

### Post by thasheep on 2006-06-06
[QUOTE=fuzzyhair]eek. I put sudo before it and it asked me for a password and i hit enter.
I dont see that folder :([/QUOTE]
You need cvs. Next you'll need (if you don't already have it) build tools.
```
sudo apt-get install cvs build-essential
```
You don't need sudo to use cvs.

---

### Post by tdrusk on 2006-06-06
[http://ubuntuforums.org/archive/index.php/t-28378.html](http://ubuntuforums.org/archive/index.php/t-28378.html)
I found that so hopefully it will help me.

---

### Post by Kilz on 2006-06-06
[QUOTE=fuzzyhair][http://ubuntuforums.org/archive/index.php/t-28378.html](http://ubuntuforums.org/archive/index.php/t-28378.html)
I found that so hopefully it will help me.[/QUOTE]


It should, its just a long explination of what the readme.txt in the linuxdcpp folder says. Its a nice version for being an alpha. I like it a lot better than Valknut, another linux client.

---

### Post by tdrusk on 2006-06-06
> Checking for C header file time.h... no
Did not find the header time.h
Can't live without it, sorry

Now what?

---

### Post by Kilz on 2006-06-06
[QUOTE=fuzzyhair]Now what?[/QUOTE]

Maybe this will help

```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by tdrusk on 2006-06-06
It's updating. Thank you for your help. I am finally starting to get an understanding of the terminal.

---

### Post by tdrusk on 2006-06-06
grr...
```
tyler@tyler-desktop:~/linuxdcpp$ sudo scons
scons: Reading SConscript files ...
Checking for None >= 3.4...Oops! No C++ compiler found!
failed
Found g++-3.4
Checking for pkg-config... ok
Checking for gtk+-2.0 >= 2.6... ok
Checking for gthread-2.0 >= 2.4... ok
Checking for libglade-2.0 >= 2.4... ok
Checking for C header file time.h... no
Did not find the header time.h
Can't live without it, sorry

```

any suggestions?

---

### Post by Kilz on 2006-06-06
[QUOTE=fuzzyhair]grr...
```
tyler@tyler-desktop:~/linuxdcpp$ sudo scons
scons: Reading SConscript files ...
Checking for None >= 3.4...Oops! No C++ compiler found!
failed
Found g++-3.4
Checking for pkg-config... ok
Checking for gtk+-2.0 >= 2.6... ok
Checking for gthread-2.0 >= 2.4... ok
Checking for libglade-2.0 >= 2.4... ok
Checking for C header file time.h... no
Did not find the header time.h
Can't live without it, sorry

```

any suggestions?[/QUOTE]

Did you add 
```
sudo apt-get install cvs build-essential
```
Like thasheep suggested?

---

### Post by grigpi on 2006-06-06
I made a deb file today, give it a try. (My first one I might add :D)

---

### Post by grigpi on 2006-06-06
Oops ... double post (I hate wireless).

---

### Post by tdrusk on 2006-06-06
Yes I think it's working now. I am getting a lot of stuff running through the terminal, so I think that is good :).

---

