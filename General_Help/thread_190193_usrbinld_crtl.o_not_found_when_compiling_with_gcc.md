---
title: "/usr/bin/ld crtl.o not found when compiling with gcc"
date: 2006-06-06
forum: General Help
---

### Post by Super Burba on 2006-06-06
I was trying to compile a few object files with gcc. Specifically, I typed "gcc -o first driver.o first.o asm_io.o" to compile an example program for using assembly with C. I got this:

/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

I tried googling it, though I couldn't find much and, being pretty new to linux in general (just installed kubuntu yesterday) I couldn't understand the stuff that seemed like it might have dealt with it.

Thanks! Sorry if I screwed up with something.

---

### Post by Super Burba on 2006-06-06
Huzzah! It's working!

I searched for the error on [www.google.com/linux](www.google.com/linux) and ended up finding a thread at [http://www.linuxforums.org/forum/debian-linux-help/34715-gcc-problem.html](http://www.linuxforums.org/forum/debian-linux-help/34715-gcc-problem.html) that at one point had a post that went

> i just did "/usr/bin/ld: crt1.o: No such file: No such file or directory" on [http://google.com](http://google.com)
 
 [http://packages.debian.org/stable/libdevel/libc6-dev](http://packages.debian.org/stable/libdevel/libc6-dev)
 
 apt-get install libc6-dev
 
 or, aptitude '/' "libc6-dev" '+' 'g' 'g'
 
So I typed "sudo apt-get install libc6-dev" and shazam!

---

### Post by hort_wort on 2007-08-31
You have saved me a great deal of effort.  Thanks much for posting the solution sir :)

---

### Post by ralphm on 2007-10-14
Thanks from me too!

---

### Post by jARLAXL on 2007-11-10
worked for me too! thanks

---

### Post by sharey on 2007-11-12
[SIZE="3"][COLOR="Indigo"][SIZE="4"]hi..
i faced the same problem when i was trying to compile a program using the 'make' command..
but when i wrote :
sudo apt-get install libc6-dev
it asked for a password
i tried to enter the password of my user name but it didnt work
what should i do please help me cuz im dealing with this problem for over a month and still couldnt fix it..
regards[/SIZE][/COLOR][/SIZE]

---

### Post by jdruin on 2007-11-21
That seemed to fix my issue as well. Could someone explain what the problem is exactly? The package has some needed files I assume but what do these files contain and how did they cause the issue? The solution is great but I would like to understand the problem and its causes as well if someone has time to explain.

---

### Post by smartCH on 2008-05-24
Installing the libc6-dev package via the synaptic package is also fine.

---

