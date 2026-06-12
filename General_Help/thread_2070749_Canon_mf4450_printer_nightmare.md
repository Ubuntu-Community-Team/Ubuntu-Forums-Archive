---
title: "Canon mf4450 printer nightmare"
date: 2012-10-13
forum: General Help
---

### Post by chadrlz on 2012-10-13
I have a canon mf4450 installed and it doesnt print or scan. This is turning into an  absolute nightmare. I am also under a deadline to get this thing working.

---

### Post by chadrlz on 2012-10-13
I got the driver package from canon and used alien to convert the rpms to debs and still no luck. Any ideas??

---

### Post by pdc on 2012-10-13
this thread

[http://ubuntuforums.org/showthread.php?t=1427330&highlight=canon&page=10](http://ubuntuforums.org/showthread.php?t=1427330&highlight=canon&page=10)

suggests you still need some 32bit packages installed;

If you copy and paste this command

> sudo apt-get install libc6-i386 ia32-libs lib32z1

that comes from post # 93 in the thread I detailed above

........... folks continually stumble with 64bit systems; I still stick to 32bit .......as it is simpler with printers................

let us know how you get along

---

### Post by chadrlz on 2012-10-13
My problem now is the scanner function. I did get it to print but now I have to remember what steps I took in what order to replicate this later today.

---

### Post by pdc on 2012-10-13
from this

[http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)

I think sane will manage your printer;

if you install xsane as a front-end ..***if not already installed*** ..

> sudo apt-get install xsane

then you should be able to scan.............

.....let us know how it goes............

I suspect if you type

> lsusb

into a terminal, your device will read as

>  ID **[COLOR="Red"]04a9:2737[/COLOR]**

---

### Post by chadrlz on 2012-10-13
I already have xsane did the backends and the extras. When I run lsusb I get 

Bus 001 Device 004: ID 04a9:2737 Canon, Inc.

---

### Post by pdc on 2012-10-13
well; if you look at the link that I gave you above;

the device MF4410 has the same ID as yours; and is described as complete support;

If you copy and paste this command

> cd /etc/udev/rules.d

and then 

> ls

..that is asking your system to list what is in that directory:

the reason I am asking this; is that this older post; 

[http://ubuntuforums.org/showthread.php?t=1427330](http://ubuntuforums.org/showthread.php?t=1427330)

talks about getting the scanner working in an [COLOR="Blue"]MF4350D[/COLOR];

by editing files in the [COLOR="Red"]rules.d[/COLOR] folder

(*when I ask what is in my system*, I get 

> 70-persistent-cd.rules   80-canon_mfp.rules   85-canon-capt.rules~
70-persistent-net.rules  85-canon-capt.rules  README


I suspect it may be of value to add to your system a file called

> 40-scanner-permissions.rules

and having changed directory to the rules.d folder, one would create this file by

> [COLOR="Red"]sudo gedit 40-scanner-permissions.rules[/COLOR]

and pasting into it what I have taken from my own Canon rules [I][B][COLOR="DarkOrchid"]but I have edited them to reflect your device
[/COLOR][/B][/I]

> [COLOR="SeaGreen"]#MF4450 printer
ATTR{idVendor}=="04a9", ATTR{idProduct}=="2737", MODE="666"[/COLOR] 

**SAVE** and **CLOSE** the text editor, gedit

......and then maybe re-boot and see if sane (xsane) now sees your device..

---

