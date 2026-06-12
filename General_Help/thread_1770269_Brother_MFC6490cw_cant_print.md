---
title: "Brother MFC6490cw cant print"
date: 2011-05-29
forum: General Help
---

### Post by Deguerrilla on 2011-05-29
I have been attempting to get my Brother printer to read on my Ubuntu Maverick 64bit system with nothing but failure.
I have downloaded all of the appropriate packages and i am now at the point where i am getting the following msg


sudo dpkg -i --force-all --force-architecture mfc6490cwlpr-1.1.2-2.i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 176291 files and directories currently installed.)
Preparing to replace mfc6490cwlpr 1.1.2-2 (using mfc6490cwlpr-1.1.2-2.i386.deb) ...
Unpacking replacement mfc6490cwlpr ...
start: Unknown job: lpd
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
start: Unknown job: lpd
dpkg: error processing mfc6490cwlpr-1.1.2-2.i386.deb (--install):
 subprocess new post-removal script returned error exit status 1
start: Unknown job: lpd
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Errors were encountered while processing:
 mfc6490cwlpr-1.1.2-2.i386.deb

---

### Post by walt.smith1960 on 2011-05-29
I don't know if it matters but I didn't include anything about force-architecture when I installed that printer on the notebook I'm typing on right now.  I downloaded the two printer .deb packages then followed the instructions here: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html). I cheated; open a terminal window and copy/paste.  I made sure to remove the parentheses when I pasted the file names.  First do the LPR then the CUPS. I didn't do step 5 or anything past it.  This may be required in earlier Ubuntu or other debian based distros. It does not seem necessary in recent Ubuntu releases.  The printer install was pretty smooth.  The scanner install with a USB cable required some research.  I don't have access to the note I made about it but I had to insert a couple lines into a SANE file somewhere for the scanner to be recognized.  Installing the scanner with a wireless network connection was better documented but the USB connection seems faster.

Edit:  Here are the notes when I installed the USB scanner:
To install the MFC-6490CW USB scanner, the following lines must be inserted in /lib/udev/rules.d/40-libsane.rules:

# Brother scanners
ATTRS{idVendor}==04f9, ENV{libsane_matched}="yes"

This applies to all users, including superusers.

---

### Post by sdibaja on 2011-08-04
I am also at a stalemate.
I run 64bit, and the drivers will not install

I am not a highly sophisticated user, I guess I need some hand holding

---

### Post by demonipuch on 2011-08-04
> **sdibaja said:**
> I am also at a stalemate.
I run 64bit, and the drivers will not install

I am not a highly sophisticated user, I guess I need some hand holding

Hello

Open a console.

Pre-required procedures :
```
sudo apt-get install ia32-libs
sudo aa-complain cupsd
sudo mkdir /usr/share/cups/model
```

Download the drivers :
```
wget http://www.brother.com/pub/bsc/linux/dlf/mfc6490cwlpr-1.1.2-2.i386.deb
wget http://www.brother.com/pub/bsc/linux/dlf/mfc6490cwcupswrapper-1.1.2-2.i386.deb
```

Install the drivers :
```
dpkg -i --force-architecture mfc6490cwlpr-1.1.2-2.i386.deb
dpkg -i --force-architecture mfc6490cwcupswrapper-1.1.2-2.i386.deb
```

Open your web browser and go to [http://localhost:631/admin/](http://localhost:631/admin/)
Enter your login and password, click the button "Add printer" and follow instructions.

---

### Post by plucky on 2011-08-04
> dpkg -i --force-architecture mfc6490cwlpr-1.1.2-2.i386.deb
dpkg -i --force-architecture mfc6490cwcupswrapper-1.1.2-2.i386.deb


The commands on the Brother Website uses **force-all** not **force-architecture**.


Good Luck

---

### Post by sdibaja on 2011-08-04
Thanks, I think I am getting close
It appears that I first need to uninstall an existing driver from previous failed attempts:

peter@peter-P170HMxPinguy:~$ sudo dpkg -i --force-architecture mfc6490cwlpr-1.1.2-2.i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
dpkg: error processing mfc6490cwlpr-1.1.2-2.i386.deb (--install):
 mfc6490cwlpr:i386 1.1.2-2 (Multi-Arch: no) is not co-installable with mfc6490cwlpr:all 1.1.2-2 (Multi-Arch: no) which is currently installed
Errors were encountered while processing:
 mfc6490cwlpr-1.1.2-2.i386.deb
----
peter@peter-P170HMxPinguy:~$ sudo dpkg -i --force-architecture mfc6490cwcupswrapper-1.1.2-2.i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
dpkg: error processing mfc6490cwcupswrapper-1.1.2-2.i386.deb (--install):
 mfc6490cwcupswrapper:i386 1.1.2-2 (Multi-Arch: no) is not co-installable with mfc6490cwcupswrapper:all 1.1.2-2 (Multi-Arch: no) which is currently installed
Errors were encountered while processing:
 mfc6490cwcupswrapper-1.1.2-2.i386.deb

------
peter@peter-P170HMxPinguy:~$ sudo dpkg -i --force-all mfc6490cwlpr-1.1.2-2.i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
dpkg: error processing mfc6490cwlpr-1.1.2-2.i386.deb (--install):
 mfc6490cwlpr:i386 1.1.2-2 (Multi-Arch: no) is not co-installable with mfc6490cwlpr:all 1.1.2-2 (Multi-Arch: no) which is currently installed
Errors were encountered while processing:
 mfc6490cwlpr-1.1.2-2.i386.deb
peter@peter-P170HMxPinguy:~$ 

----------
peter@peter-P170HMxPinguy:~$ sudo dpkg -i --force-all mfc6490cwcupswrapper-1.1.2-2.i386.deb 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
dpkg: error processing mfc6490cwcupswrapper-1.1.2-2.i386.deb (--install):
 mfc6490cwcupswrapper:i386 1.1.2-2 (Multi-Arch: no) is not co-installable with mfc6490cwcupswrapper:all 1.1.2-2 (Multi-Arch: no) which is currently installed
Errors were encountered while processing:
 mfc6490cwcupswrapper-1.1.2-2.i386.deb
peter@peter-P170HMxPinguy:~$ 


How do I uninstall? :(:(:(

---

### Post by plucky on 2011-08-05
> How do I uninstall? 

Use Synaptic Package Manager

---

### Post by sdibaja on 2011-08-05
Thanks demonipuch and plucky!

Success!  It works:popcorn:

---------- my synopsis of instructions ------------

Brother MFC6490cw 64bit printer driver instalation
-----
Open a console.

Pre-required procedures :

Code:
sudo apt-get install ia32-libs
sudo aa-complain cupsd
sudo mkdir /usr/share/cups/model

Download the drivers :
Code:
wget [http://www.brother.com/pub/bsc/linux/dlf/mfc6490cwlpr-1.1.2-2.i386.deb](http://www.brother.com/pub/bsc/linux/dlf/mfc6490cwlpr-1.1.2-2.i386.deb)
wget [http://www.brother.com/pub/bsc/linux/dlf/mfc6490cwcupswrapper-1.1.2-2.i386.deb](http://www.brother.com/pub/bsc/linux/dlf/mfc6490cwcupswrapper-1.1.2-2.i386.deb)

Install the drivers :
Code:
sudo dpkg -i --force-all mfc6490cwlpr-1.1.2-2.i386.deb
sudo dpkg -i --force-all mfc6490cwcupswrapper-1.1.2-2.i386.deb

Open your web browser and go to [http://localhost:631/admin/](http://localhost:631/admin/)
Enter your login and password, click the button "Add printer" and follow instructions.

---

### Post by Deguerrilla on 2011-09-26
i have repeatedly tried this to no avail. 
When i attempt to force all/ force architecture i get the following msgs:

Unpacking replacement mfc6490cwlpr:i386 ...
start: Unknown job: lpd
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
start: Unknown job: lpd
dpkg: error processing mfc6490cwlpr-1.1.2-2.i386.deb (--install):
 subprocess new post-removal script returned error exit status 1
start: Unknown job: lpd
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Errors were encountered while processing:
 mfc6490cwlpr-1.1.2-2.i386.deb

After i get this msg i still tried to move fwd only to get this msg:


dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 184830 files and directories currently installed.)
Preparing to replace mfc6490cwcupswrapper:i386 1.1.2-2 (using mfc6490cwcupswrapper-1.1.2-2.i386.deb) ...
Unpacking replacement mfc6490cwcupswrapper:i386 ...
dpkg: dependency problems prevent configuration of mfc6490cwcupswrapper:i386:
 mfc6490cwcupswrapper:i386 depends on mfc6490cwlpr; however:
  Package mfc6490cwlpr:i386 is not installed.
dpkg: error processing mfc6490cwcupswrapper:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mfc6490cwcupswrapper:i386

Any help would be awesome

---

