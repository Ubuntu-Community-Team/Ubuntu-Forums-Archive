---
title: "Software Center stuck &quot;Applying Changes&quot;"
date: 2010-03-07
forum: General Help
---

### Post by Deadseraph on 2010-03-07
I've been trying to install software from the software center, and I'm running into some interesting issues.  The biggest one is that my software center repeatedly gets stuck at some odd percentage while "Applying Changes" and never moves again.  The software seems to install fine, but it's impossible to install more software without restarting the computer to clear the queue.  I've tried "sudo dpkg --configure -a", but it says the status database area is locked by another process.  I have no idea what to do and I really don't feel like installing all over again, so any advice would be greatly appreciated.

---

### Post by Deadseraph on 2010-03-07
I Re-Started the system, tried running a sudo dpkg --configure -a, and it said there's some issue with the installation of my java jdk, suggestions on how to fix it?

---

### Post by patchwork on 2010-03-07
```
sudo apt-get install -f

```...though I think that it is similar in function to dpkg --configure -a

---

### Post by Sharang.d on 2010-06-14
I have the same problem as the topic starter.
The Program is "Avast!" i suppose which is stuck while removal so i cannot even run any apt-get commands nor can i open the Package Manager. So basically i cannot add/remove/modify any Packages even after Logging Out/In and Restarting the PC!

Please help asap.
Thank You!

---

### Post by Bucic on 2011-01-24
Same here. Installation of every app will "hang" because of some "problems in the past" with another package:

```
installArchives() failed: Selecting previously deselected package libsdl-gfx1.2-4. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 145843 files and directories currently installed.) 
Unpacking libsdl-gfx1.2-4 (from .../libsdl-gfx1.2-4_2.0.20-1_i386.deb) ... 
Selecting previously deselected package libsdl-net1.2. 
Unpacking libsdl-net1.2 (from .../libsdl-net1.2_1.2.7-2_i386.deb) ... 
Selecting previously deselected package ttf-vlgothic. 
Unpacking ttf-vlgothic (from .../ttf-vlgothic_20100416-2_all.deb) ... 
Selecting previously deselected package wormux-data. 
Unpacking wormux-data (from .../wormux-data_1%3a0.9.2.1-0ubuntu1_all.deb) ... 
Selecting previously deselected package wormux. 
Unpacking wormux (from .../wormux_1%3a0.9.2.1-0ubuntu1_i386.deb) ... 
Processing triggers for fontconfig ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for man-db ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for python-support ... 
Setting up firmware-b43-installer (4.150.10.5-4) ... 
--2011-01-25 03:31:02--  http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2 
Resolving mirror2.openwrt.org... 46.4.11.11 
Connecting to mirror2.openwrt.org|46.4.11.11|:80... failed: Connection timed out. 
Retrying. 
 
--2011-01-25 03:31:24--  (try: 2)  http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2 
Connecting to mirror2.openwrt.org|46.4.11.11|:80... failed: Connection timed out. 
Retrying. 
 
.
.
.

Retrying. 
 
--2011-01-25 03:39:36--  (try:19)  http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2 
Connecting to mirror2.openwrt.org|46.4.11.11|:80... failed: Connection timed out. 
Retrying. 
 
--2011-01-25 03:40:07--  (try:20)  http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2 
Connecting to mirror2.openwrt.org|46.4.11.11|:80... failed: Connection timed out. 
Giving up. 
 
dpkg: error processing firmware-b43-installer (--configure): 
 subprocess installed post-installation script returned error exit status 4 
Setting up libsdl-gfx1.2-4 (2.0.20-1) ... 
No apport report written because MaxReports is reached already
Setting up libsdl-net1.2 (1.2.7-2) ... 
Setting up ttf-vlgothic (20100416-2) ... 
Setting up wormux-data (1:0.9.2.1-0ubuntu1) ... 
Setting up wormux (1:0.9.2.1-0ubuntu1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 firmware-b43-installer 
Setting up firmware-b43-installer (4.150.10.5-4) ... 
--2011-01-25 03:40:33--  http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2 
Resolving mirror2.openwrt.org... 46.4.11.11 
Connecting to mirror2.openwrt.org|46.4.11.11|:80... failed: Connection timed out. 
Retrying. 
 
--2011-01-25 03:40:55--  (try: 2)  http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2 
Connecting to mirror2.openwrt.org|46.4.11.11|:80... failed: Connection timed out. 
Retrying. 
 
.
.
.
 
--2011-01-25 03:49:38--  (try:20)  http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2 
Connecting to mirror2.openwrt.org|46.4.11.11|:80... failed: Connection timed out. 
Giving up. 
 
dpkg: error processing firmware-b43-installer (--configure): 
 subprocess installed post-installation script returned error exit status 4 
Errors were encountered while processing: 
 firmware-b43-installer 
```

In the meantime, can we change the number of retries from 20 to e.g. 3?

---

### Post by gedthecreator on 2011-02-15
After a bit of playing around I discovered that the EULA pops up behind the Software Centre. Not sure if this is the same problem everyone else is having but it sorted out my issues.

---

### Post by Bucic on 2011-02-15
> **gedthecreator said:**
> After a bit of playing around I discovered that the EULA pops up behind the Software Centre. Not sure if this is the same problem everyone else is having but it sorted out my issues.
I think others were not that lucky. See my messed up case and others probably stumbled upon something similar too. So generally it's a good idea to use ***sudo apt-get ...*** in the terminal to be able to see all potential errors.

---

