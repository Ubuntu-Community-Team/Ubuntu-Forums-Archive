---
title: "Installing 32bit app.  Wrong ELF Class: ELFCLASS64"
date: 2011-07-30
forum: General Help
---

### Post by YellowHammer on 2011-07-30
I am trying to install Ember on 11.04-64bit.  I can find very little support for Ember from their website.  When I try to install by typing:
./Ember-0.6.1.1

I get this error:

./Ember-0.6.1.1: error while loading shared libraries: libfuse.so.2: wrong ELF class: ELFCLASS64

Are there any suggestions for getting this to work?

---

### Post by galvatron408 on 2011-07-30
you said you're on a 64-bit system and then you said you're installing a 32 bit app and then you said the error is that it's the wrong ELF class "ELFCLASS64".

Sooooo, that means, your 32-bit application can't use a 64 bit library and that's just the way it is.

you can still try to run it if you have the 32-bit library. I have it.
file /lib/libfuse.so.2.8.4 
/lib/libfuse.so.2.8.4: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped

If you have it, set your LD_LIBRARY_PATH to /lib and try it again. Just type...

export LD_LIBRARY_PATH=/lib

from wikipedia:
$LD_LIBRARY_PATH On many Unix systems with a [dynamic linker]("http://en.wikipedia.org/wiki/Dynamic_linker"), contains a colon-separated list of directories that the dynamic linker should search for [shared objects]("http://en.wikipedia.org/wiki/Shared_object") when building a process image after exec, before searching in any other directories.

---

### Post by YellowHammer on 2011-07-30
My lib is 64bit.  So is there anyway to install the 32bit lib?

file /lib/libfuse.so.2.8.4
/lib/libfuse.so.2.8.4: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped

---

### Post by jocko on 2011-07-30
> **YellowHammer said:**
> My lib is 64bit.  So is there anyway to install the 32bit lib?

file /lib/libfuse.so.2.8.4
/lib/libfuse.so.2.8.4: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped

Try getlibs:
```
sudo apt-get install getlibs
```
Then:
```
sudo getlibs ./Ember-0.6.1.1
```
Or:
```
sudo getlibs -l libfuse.so
```

---

### Post by YellowHammer on 2011-07-30
Can't locate getlibs.... :confused:


```
michael@umichael:~/Downloads$ sudo apt-get install getlibs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package getlibs
```

---

### Post by jocko on 2011-07-31
> **YellowHammer said:**
> Can't locate getlibs.... :confused:


```
michael@umichael:~/Downloads$ sudo apt-get install getlibs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package getlibs
```
Hmmm... Weird. I can't remember installing it in my system, but I have it... Must have gotten it from some ppa I'm not using anymore...
The only place I can find it is here: [http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/) and a thread about it here: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by Gyokuro on 2011-07-31
you need ia32-libs on a 64-Bit system

sudo apt-get install ia32-libs

---

### Post by YellowHammer on 2011-08-03
> **Gyokuro said:**
> you need ia32-libs on a 64-Bit system

sudo apt-get install ia32-libs

Thanks.  I had already done this, but it did not fix it. I tried again just in case, and still didn't work. :(

---

### Post by YellowHammer on 2011-08-03
> **jocko said:**
> Hmmm... Weird. I can't remember installing it in my system, but I have it... Must have gotten it from some ppa I'm not using anymore...
The only place I can find it is here: [http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/) and a thread about it here: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)


Perfect. Thank you!

---

