---
title: "uninstalling/installing aircrack-ng with sqlite support"
date: 2009-12-15
forum: General Help
---

### Post by redlinethecar on 2009-12-15
Ok let me start out with my system specs.  
Ubuntu 9.10 (kermic)
Gnome 2.28.1
kernel 2.6.31-16
GCC version 4.4.1 (x86_64-linux-gnu)
AMD Turion(tm) II Ultra Dual-Core Mobile M620

Firstly I installed aircrack-ng by using "sudo apt-get install aircrack-ng"
After realising that I cannot use a database with this version I set out and searched for aircrack-ng-1.0-rc4
After finding this version I uninstalled aircrack by typing 
sudo apt-get remove aircrack-ng and boom it was gone.
then i ran
sudo apt-get install sqlite3
then i went into the aircrack-ng-1.0-rc4 directory and ran
sudo make sqlite=true sqlite=unstable
sudo make sqlite=true sqlite=unstable install

now when loading the database into aircrack using -r I get the same error, 
Error: Aircrack-ng wasn't compiled with sqlite support.

What am i missing here i compiled with no errors????? cant figure it out

---

### Post by cj13579 on 2009-12-15
Have you read the release notes? You may have to specify that you wish to enable SQLite when you compile the program. Something like:

```
./configure --enable-sqlite
```

---

### Post by redlinethecar on 2009-12-15
really sorry for double posting, but i realised that the command i entered to install sqlite3 was

sudo apt-get install sqlite3 libsqlite3-dev

don't know if that makes a difference.

---

### Post by redlinethecar on 2009-12-15
digital@digital-laptop:~/Desktop/aircrack-ng-1.0-rc4$ ./configure --enable-sqlite
bash: ./configure: No such file or directory


Is this supposed to be executed in the aircrack-ng directory before install?  Or elsewhere?

---

### Post by cj13579 on 2009-12-15
That example would have to be run before installation and presumes that you are compiling and installing from the source code. I have never installed the software myself but that would be my first thought. Failing that it may have a .conf in /etc where you can edit settings.

---

### Post by redlinethecar on 2009-12-15
Ok well i appreciate the help and I figured it out.  all i did was run a 
make clean
and reinstalled and it seems to be working fine now.

---

### Post by cj13579 on 2009-12-15
Nice, that was simple!

---

### Post by dysaan on 2010-06-11
Hello, I'm a noob. There I've said it. That aside I know my way around windows but linux is driving me nuts. I've gone from forum to forum for 2 weeks now and gotten nowhere. 
In trying to get set-up and online with a desktop computer I have had no luck. 
I have a awus036nh wireless usb which by all accounts is compatable. 
 
I have downloaded and installed ubuntu 10? ( newest ) which did recognize the wireless after some prompting but ... we'll get back to that.
 
I also downloaded vmware version and installed it which says it see's and attaches my wireless but won't use it to find any signal claiming there is nothing there after-all. No clue how to fix that.
 
I made a live cd of backtrack3 ( compatable with my wireless ) doesn't find it at all. Useless hours of forums and toying to get nowhere.
 
Back to ubuntu which at least recognizes my wireless device and shows signals ... figured I'd try aircrack/airdump/airoscript ... yes I'm curious as to how this works out... downloaded aircrack and kismet to a usb drive and dragged them to my ubuntu desktop. Now what? command code sudo apt-get install aircrack-ng ( nothing ) it doesn't show up with a search via the synaptic search either. How do you load a program into this system. There are no run / install commands in the download like in windows programs so how do you get to do anything but look at a bunch of files with this?
It's very frustrating and I can see from the forums that I'm far from the only one experiencing these hang-ups.
Any help would be appreciated. Even if I need to start over from scratch. 
Please remember I'm a babe in the woods here. Slow and informative helps. 
IE: I had to figure out what a "shell" was and how to access it. ( but I did it )
I'm trying to expand my horizons here, but it's got to meet me a little bit of half way.
 
Great tutorials exist for already set up and working systems but nothing on how to set it up from GO that i've found useful.
Again thank you for any help and patience you can supply. We all have to start somewhere.

---

### Post by mklyuzhev on 2010-12-21
dysaan, are you still looking for directions?

---

