---
title: "how do i install Automatix"
date: 2006-02-01
forum: General Help
---

### Post by uBuNtuh4x on 2006-02-01
im very very new to linux...come someone do a step by step plese

---

### Post by happyponcho42 on 2006-02-01
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by uBuNtuh4x on 2006-02-01
k this is what i put into terminal...

john@ubuntu:~$ sudo apt-get install xterm
Password:
Reading package lists... Done
Building dependency tree... Done
xterm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
john@ubuntu:~$ wget [http://beerorkid.com/automatix/automatix_5.1-1_i386.deb](http://beerorkid.com/automatix/automatix_5.1-1_i386.deb)
--16:29:44--  [http://beerorkid.com/automatix/automatix_5.1-1_i386.deb](http://beerorkid.com/automatix/automatix_5.1-1_i386.deb)
           => `automatix_5.1-1_i386.deb.2'
Resolving beerorkid.com... 205.196.218.206
Connecting to beerorkid.com|205.196.218.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 32,200 (31K) [text/plain]

100%[====================================>] 32,200       110.79K/s

16:29:49 (110.78 KB/s) - `automatix_5.1-1_i386.deb.2' saved [32200/32200]

john@ubuntu:~$ sudo dpkg -i automatix_5.1-1_i386.deb
dpkg: error processing automatix_5.1-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 automatix_5.1-1_i386.deb
john@ubuntu:~$ sudo dpkg -i automatix_5.1-1_i386.deb
dpkg: error processing automatix_5.1-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 automatix_5.1-1_i386.deb
john@ubuntu:~$


im not sure if i did it right...

i dont think it is beacuse it says: package architecture (i386) does not match system (amd64)
Errors were encountered while processing:

help?

---

### Post by arnieboy on 2006-02-01
[QUOTE=uBuNtuh4x]k this is what i put into terminal...

john@ubuntu:~$ sudo apt-get install xterm
Password:
Reading package lists... Done
Building dependency tree... Done
xterm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
john@ubuntu:~$ wget [http://beerorkid.com/automatix/automatix_5.1-1_i386.deb](http://beerorkid.com/automatix/automatix_5.1-1_i386.deb)
--16:29:44--  [http://beerorkid.com/automatix/automatix_5.1-1_i386.deb](http://beerorkid.com/automatix/automatix_5.1-1_i386.deb)
           => `automatix_5.1-1_i386.deb.2'
Resolving beerorkid.com... 205.196.218.206
Connecting to beerorkid.com|205.196.218.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 32,200 (31K) [text/plain]

100%[====================================>] 32,200       110.79K/s

16:29:49 (110.78 KB/s) - `automatix_5.1-1_i386.deb.2' saved [32200/32200]

john@ubuntu:~$ sudo dpkg -i automatix_5.1-1_i386.deb
dpkg: error processing automatix_5.1-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 automatix_5.1-1_i386.deb
john@ubuntu:~$ sudo dpkg -i automatix_5.1-1_i386.deb
dpkg: error processing automatix_5.1-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 automatix_5.1-1_i386.deb
john@ubuntu:~$


im not sure if i did it right...

i dont think it is beacuse it says: package architecture (i386) does not match system (amd64)
Errors were encountered while processing:

help?[/QUOTE]


yes automatix is only for systems running x86 packages. it wont work on AMD64 or ppc systems. this is clearly mentioned at the top of the first post in the automatix thread.

---

### Post by uBuNtuh4x on 2006-02-01
well...is there any alturnative for me? could i install ubuntu witha version that suports it even tho i have a 64-bit processor?

or is there anythin for amd 64?

---

### Post by AmboyGuy on 2006-02-01
You're at the cutting edge of technology with a 64 bit CPU. There aren't a lot of people (including developers) who are currently using the latest & greatest hardware. Maybe in a year or so the software tools will catch up to the hardware. Windows XP 64 bit, when it finally was available, didn't exactly break any sales records.

Why don't you give yourself three months using & learning 32 bit linux and then load up the cutting edge, dual core 12Ghz 64 bit hyper houdini version. By that time new software tools & better support will be available and you'll have learned some of the basics of linux.

I'm running an i686 kernel on a 450Mhz P3 with 128MB of RAM. That's a fairly big enough challenge for anyone. My biggest advantage is that a lot of people have 'been there, done that' and left enough tracks for me to follow.

---

### Post by astronerd on 2006-02-01
Well there isnt anything as easy as automatix for 64 bit, at least not that I know of.  But here is a site that has ALOT of answers to common questions along with a very simple way of installing pretty much anything you could want for your ubuntu box.  (Im assuming you are running 5.10 right?)
  [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

Hope this helps..

---

