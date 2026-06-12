---
title: "installed build essentials"
date: 2006-05-29
forum: General Help
---

### Post by bobanshirl on 2006-05-29
Can someone please tell me word by word how to find out what build essentials are installed with Breezy Badger and also how would I install same if they are not installed.I am presently reading a post re Internal Winmodem Woes by towsonu2003.I wish I could telephone or email towsonu2003 because he says to download packages (have not a clue what packages)but to make sure the dependencies are installed (have not got a clue where what or why) I have said this before but most answers to threads use technical jargon and I am 71 yrs and have not got a degree in computers certainly not Linux if you are out there towsonu2003 please contact you are my last resort before I call it a day.

---

### Post by Perfect Storm on 2006-05-29
To install it:

```
sudo apt-get install build-essential
```

It install thte common tools for compiling:  libc6-dev, gcc, g++, make and dpkg-dev.

---

### Post by vinodis on 2006-05-29
please dont repeat these things again and again.. this install instructions dont work without an internet connection on the machine. If you try to make a manual installation of build-essential package by downloading the specified .deb files, the dependencies are not just one level but multiple levels and its too cumbersome. I dont know why dont Ubuntu Team make it as a standard feature to include it. I tried many a times to get the Build-Essentials installed on my machine without internt connection by downloading individual depended .deb files and failed. 
I finally decided not to compile.. :(

---

### Post by Perfect Storm on 2006-05-29
It's because it's to big to be on the CD (around 86MB as I recall it)

---

### Post by canci on 2006-05-29
:confused: 

yes, i have to complain about it as well. I had similar problems while compiling fluxbox.
you could probably throw out loads of those games or similar and add up those very essential things.
I mean, what is the point of having Linux and not being able to compile?
Futile somehow.
Then the Ubuntu team should clearly state that the distro is for broadband users only. I think stretching the distro onto 2 CDs wouldn't be a bad compromise either.
Every beginner should learn compiling, and, as far as I got this, Ubuntu IS a distro that wants ppl to get into Linux.

](*,) 

Think about it, oh great Ubunturinos! ;)

---

### Post by az on 2006-05-29
[QUOTE=vinodis]please dont repeat these things again and again.. this install instructions dont work without an internet connection on the machine. If you try to make a manual installation of build-essential package by downloading the specified .deb files, the dependencies are not just one level but multiple levels and its too cumbersome. I dont know why dont Ubuntu Team make it as a standard feature to include it. I tried many a times to get the Build-Essentials installed on my machine without internt connection by downloading individual depended .deb files and failed. 
I finally decided not to compile.. :([/QUOTE]


Build-essential is on the install cd.  You do not need to be on the net to get it, it will prompt you to insert your cd again and will install from there, if it is not already cached on your hard drive.

The fact that gcc-4.0 is shipped, and everyting except the kernel is compiled with gcc-4.0 is an oops.  You need gcc-3.4 to compile kernel stuff, and *that* is not on the cd.  You need to get three packages.

Even the Dapper Desktop (live) cd ships with a repository on it that includes build-essential and everything else you need to build extra kernel drivers (yes, the kernel is now built with gcc-4.0)

---

### Post by Perfect Storm on 2006-05-29
Okay, didn't knew that, must be because I turn off the CD sourcelist when ubuntu is installed.

---

### Post by 2501 on 2006-05-29
hi.

I am using fluxbox right now and I did not have any problem during installation. I just had to download the libraries and that was all. 

let me know if you are having problems.

-2501

---

