---
title: "Problem with Ubuntu 10.04 make command"
date: 2010-06-26
forum: General Help
---

### Post by jamdoc on 2010-06-26
Can someone help me? I am getting the following error when I try to issue the 'make' command. 

>sudo make
make: -F.: Command not found
/bin/sh: Illegal option - 
/bin/sh: Illegal option - 
/bin/sh: Illegal option - 
/bin/sh: Illegal option - 
/bin/sh: Illegal option - 
/bin/sh: Illegal option - 
/bin/sh: Illegal option - 
/bin/sh: Illegal option - 
/bin/sh: Illegal option - 
/bin/sh: Illegal option - 
/bin/sh: Illegal option - 
****
**** The configure script must be executed before running 'make'.
****               Please run "./configure".
****
make: *** [makeopts] Error 1

---

### Post by linorics on 2010-06-26
1.) Do you have build-essentials installed?
```
sudo apt-get install build-essential
``` 

2.) Did you run the configure script 
```

sudo chmod +x configure
sudo ./configure

```

---

### Post by jamdoc on 2010-06-26
After running "sudo apt-get install build-essentials", I got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essentials

Also "sudo ./configure" ran and ends with:

configure: *** XML documentation will not be available because the 'libxml2' development package is missing.
configure: *** Please run the 'configure' script with the '--disable-xmldoc' parameter option
configure: *** or install the 'libxml2' development package.

---

### Post by linorics on 2010-06-26
Sorry type in the last post
```
sudo apt-get install build-essential
```

Try this for libxml2
```
sudo apt-get install libxml2
```

---

### Post by jamdoc on 2010-06-27
I have entered the commands and received the outputs below. However, the problem still exist when the "make" command was executed after.

> sudo apt-get install build-essential

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

> sudo apt-get install libxml2

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxml2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

---

### Post by mc4man on 2010-06-27
use this
```
sudo apt-get install libxml2-dev
```

Generally speaking you don't need (or want) to run a ./configure and make as root, only the make install. (there are exceptions

If you continue to have issues maybe put into context - post complete terminal output inc. command(s) and if you wish what source you're trying to build and install

---

### Post by jamdoc on 2010-06-27
I am compiling asterisk-1.4.33.1 in the /usr/src directory. The commands above did not make any difference.
I am now using the root login and having executed the "make install" command, I got the following message:

make: -F.: Command not found
****
**** The configure script must be executed before running 'make'.
****               Please run "./configure".
****
make: *** [makeopts] Error 1

---

### Post by mc4man on 2010-06-27
If you're going to build in /usr then you'll need to run a commands as root - why you are doing so I'm not sure.

Otherwise - do as it says, run a ./configure first and pass it.

there is a readme in the source you may want to look at.

Happen to be on a live cd atm and had built a few sources - your's went quite easily (built in home dir. - no sudo

>  ,,,,,,,,,,,,,,,,,
+--------- Asterisk Build Complete ---------+
 + Asterisk has successfully been built, and +
 + can be installed by running:              +
 +                                           +
 +               make install                +
 +-------------------------------------------+
ubuntu@ubuntu:~/Downloads/asterisk-1.4.33.1$ 


---

### Post by gadolinio on 2010-06-28
> **mc4man said:**
> If you're going to build in /usr then you'll need to run a commands as root - why you are doing so I'm not sure.

Right, this is a good point. Can you run the commands in your home directory? Why do you need to do it in /usr?  And using the root login is generally not recommended.

> **mc4man said:**
>   
do as it says, run a ./configure first and pass it.
(...)
there is a readme in the source you may want to look at.

+1. The common way to go is, once you're in the directory of the source code, and have execution permission for the "configure" file:
```

./configure

```
Right after it finishes (if there are no errors reported):
```

sudo make

```
And finally:
```

sudo checkinstall

```
(you might see "sudo make install" more often, but checkinstall is easier to manage later).
Good luck!

---

### Post by jamdoc on 2010-06-28
Thanks, I seem to have been ignoring the error reported when ./configure ran. This was "libncurses5-dev", which I then installed (sudo apt-get install libncurses5-dev) and then ran "./configure" again - which was successful. 

"sudo make" ran without any error.

Thanks again.

---

### Post by gadolinio on 2010-06-28
> **jamdoc said:**
> Thanks, I seem to have been ignoring the error reported when ./configure ran. This was "libncurses5-dev", which I then installed (sudo apt-get install libncurses5-dev) and then ran "./configure" again - which was successful. 

"sudo make" ran without any error.

Thanks again.

You're welcome! Please remember to mark the thread as "solved".

---

