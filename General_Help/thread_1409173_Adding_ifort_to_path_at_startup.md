---
title: "Adding ifort to path at startup"
date: 2010-02-17
forum: General Help
---

### Post by Raff1 on 2010-02-17
Hello! I just downloaded intel's fortran compiler, ifort. However, I seem to have to add it to path for every single terminal I open using:

```

source <install-dir>/bin/ifortvars.sh <arg>

```

I immediately think that there should be a way of doing this automatically at startup. However, this isnt just pointing to where ifort is, but running a shell script, which evidently only affects a single terminal session. Any helpful suggestions will be appreciated! :)

---

### Post by rnerwein on 2010-02-17
hi
if you are using a bash shell put it in your ~/.bashrc those instructions will run for every terminal you open.
or you want to have it for every login system wide put a script in /etc/profile.d
ciao

---

### Post by Raff1 on 2010-02-17
> **rnerwein said:**
> if you are using a bash shell put it in your ~/.bashrc those instructions will run for every terminal you open.

It worked (ofc)! :D You made my day ;)

> **rnerwein said:**
> or you want to have it for every login system wide put a script in /etc/profile.d
So I could have added a shell script containing the desired line there. What do you meen by with "every login system wide"? Is it for every user (account)? For surely what I did only applies for my own user. Thanks again!

- EDIT - spelling

---

### Post by rnerwein on 2010-02-17
hi
with "every login system wide" i mean that if you put it in the /etc/profile.d this will work for every body who logs in into the box because scripts wich are locatet there will run for every login ( every user) into your system.
ciao

---

### Post by krohit_20 on 2011-02-12
guys plz tell me how to do that scripting buisness
im new to ubunutu and i installed ifort composer xe 2011 for linux
installation went well...
but the ifort command in terminal is not recognized. 
how to get it working ?

---

### Post by Raff1 on 2011-04-11
I just consulted this old thread again to see how I added ifort to path back then :P

What I did was merely what was suggested above in the thread. Editing the ~/.bashrc was the easiest option for me. It can be found in your home-folder and its hidden. Ctrl+H to show hidden files. Then I added the following lines at the bottom:

```
# Adding ifort to path at the beginning of every terminal session
source /opt/intel/bin/compilervars.sh intel64
```If you are using 32-bit compiler, replace intel64 with ia32. If compilervars.sh is located an other place than /opt/intel/bin, the path must ofc be updated as well.

---

