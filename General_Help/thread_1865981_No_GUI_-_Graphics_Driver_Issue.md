---
title: "No GUI - Graphics Driver Issue"
date: 2011-10-20
forum: General Help
---

### Post by rusty spork on 2011-10-20
I had a perfectly fine 11.04 system, but I needed more storage space for a project I am working on.  I ended up wiping my drive reallocating my partitions and doing a full reinstall of windows and ubuntu to try and squeeze some more space out of my outdated HD.

I spent 10-15 hours installing all the software I needed for my projects including 12+ GB of nuclear data that I will need.  I ran updates restarted several times and got everything working perfectly.

The next morning I booted my computer and ubuntu won't load any GUI-I can ctrl-alt-f1 and get to a terminal.  I've just barely been scraping by through the command line and using campus computers (windows works fine, but I only have linux software), but I really need to get my computer working.  I really don't know what to do and I can't afford to spend the time to get all the software working again.  Guidance and any help you may have to offer would me much appreciated, thank you.

---

### Post by dcstar on 2011-10-21
> **rusty spork said:**
> 
..........
The next morning I booted my computer and ubuntu won't load any GUI-I can ctrl-alt-f1 and get to a terminal.  I've just barely been scraping by through the command line and using campus computers (windows works fine, but I only have linux software), but I really need to get my computer working.  I really don't know what to do and I can't afford to spend the time to get all the software working again.  Guidance and any help you may have to offer would me much appreciated, thank you.

Do a search for the hundreds of other threads who report "blank screen" etc.

---

### Post by rusty spork on 2011-10-21
I searched and tried several different things already...in any case I ended up doing a full reinstall, and am avoiding activating any of the nvidia drivers until I have more time to figure out this issue.

---

### Post by rusty spork on 2011-10-23
Okay...I don't have a clue what's causing the problem this time, but I am currently getting a looping log in screen...

[Before I had no graphics at all; I had a looping log in, then no log in (dark purple screen), then no screen at all. In all cases I had access to a command prompt]

I have tried:

-logging in with classic/classic(no effects)/safe mode.
-Creating a new account with admin privileges.
-logging in from terminal then $startx
-Updating gdm
-Installing kdm (instead of gdm).
-deleting the /etc/X11/xinit directory.
   And adding the two following directories:
     /etc/X11/xinit/xinitrc.d
     /etc/X11/xinit/xinput.
-https://bugs.launchpad.net/ubuntu/+source/samba/+bug/292791
-deleting samba and samba-common


None of these have worked; I just found this bug report and am going to try it:

[https://bugs.launchpad.net/ubuntu/+source/gnupg2/+bug/766574](https://bugs.launchpad.net/ubuntu/+source/gnupg2/+bug/766574)

---

### Post by oldtimer7777 on 2011-10-24
Which version of Ubuntu are you trying to install fresh?

> **rusty spork said:**
> Okay...I don't have a clue what's causing the problem this time, but I am currently getting a looping log in screen...

[Before I had no graphics at all; I had a looping log in, then no log in (dark purple screen), then no screen at all. In all cases I had access to a command prompt]

I have tried:

-logging in with classic/classic(no effects)/safe mode.
-Creating a new account with admin privileges.
-logging in from terminal then $startx
-Updating gdm
-Installing kdm (instead of gdm).
-deleting the /etc/X11/xinit directory.
   And adding the two following directories:
     /etc/X11/xinit/xinitrc.d
     /etc/X11/xinit/xinput.
-https://bugs.launchpad.net/ubuntu/+source/samba/+bug/292791
-deleting samba and samba-common


None of these have worked; I just found this bug report and am going to try it:

[https://bugs.launchpad.net/ubuntu/+source/gnupg2/+bug/766574](https://bugs.launchpad.net/ubuntu/+source/gnupg2/+bug/766574)

---

### Post by rusty spork on 2011-10-24
Right now I'm using 11.04.  I'd like to avoid updating 11.10 as I was having the same problems, also I'm not a fan of unity or gnome 3.

Tried that last bug fix I posted previously, the file /.xsession-errors and the directory /home/user/.gnupg....  don't exist.  Tried searching to see if xsession-errors is located somewhere else, couldn't find anything.

I've been using ubuntu for the past few years, and after the past couple weeks of this, I'm starting to become somewhat familiar with the command line.

---

### Post by oldtimer7777 on 2011-10-24
If I was you... the first plan of attack would be to get a viable running system on that hard drive somehow. 

Try 10.10..  

[http://debianhelp.wordpress.com/2011/07/05/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://debianhelp.wordpress.com/2011/07/05/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

Squeeze down the size of your 11.04 partition with Gparted using a live stick of Ubuntu 10.10..  Then install 10.10 to that new partition. Once you have 10.10 installed you will have access to your files and folders on 11.04...  You will have most of your work there..   I don't know what kind of applications but the walkthrough will guide you through most of the common applications you would need.

> **rusty spork said:**
> Right now I'm using 11.04.  I'd like to avoid updating 11.10 as I was having the same problems, also I'm not a fan of unity or gnome 3.

Tried that last bug fix I posted previously, the file /.xsession-errors and the directory /home/user/.gnupg....  don't exist.  Tried searching to see if xsession-errors is located somewhere else, couldn't find anything.

I've been using ubuntu for the past few years, and after the past couple weeks of this, I'm starting to become somewhat familiar with the command line.

---

### Post by rusty spork on 2011-10-24
I wish I could-I only have about 5 GB of extra space on my tiny hard drive (several compilers, matlab, AerE software, etc...).  And windows is already as minimal as I can get it.  If installing a new OS is my only option, I might as well just wipe the whole partition and start over.

With all the time that I've put into this, I could have walked myself through an install of Gentoo by now (planning to over winter break).

I'll probably wait a little longer for other options if you don't mind.  There has to be a fix for this.

---

### Post by oldtimer7777 on 2011-10-24
Sound like you need to install more hard drive space actually.  You can pick up a half Tb HDD for around 50 bucks on Ebay. Clonezilla everything you got over to the new hard drive.   Heck, I would even go for for a full 1Tb Sata drive if you have the money.

> **rusty spork said:**
> I wish I could-I only have about 5 GB of extra space on my tiny hard drive (several compilers, matlab, AerE software, etc...).  And windows is already as minimal as I can get it.  If installing a new OS is my only option, I might as well just wipe the whole partition and start over.

With all the time that I've put into this, I could have walked myself through an install of Gentoo by now (planning to over winter break).

I'll probably wait a little longer for other options if you don't mind.  There has to be a fix for this.

---

### Post by rusty spork on 2011-10-24
I wish I could buy a new drive, but it just isn't an option.

[If space is the issue, I guess I'll be living in the linux lab this semester...]

How can I know for sure?  Wouldn't there be some error file somewhere that would report a space problem?

---

### Post by oldtimer7777 on 2011-10-24
> **rusty spork said:**
> I wish I could buy a new drive, but it just isn't an option.

[If space is the issue, I guess I'll be living in the linux lab this semester...]

How can I know for sure?  Wouldn't there be some error file somewhere that would report a space problem?

Well, you mentioned that you have compressed Windows down as small as you can in its own partition.  What I would probably do instead is ditch Windows. Pick an OS, and use Wine to emulate the few apps from Windows I still need to run for work or school. Figure out just what I need from Windows on Ubuntu and see if I can't get them to install and run correctly for myself in Ubuntu natively.  PlayOnLinux runs so many Windows Apps than before that I couldn't get installed on Ubuntu to run correctly and smoothly. Now they run great with PlayOnLinux... You might be surprised. If upgrading your hard drive isn't a solution right now, maybe picking an OS to be the one you use from now on instead, and open up that free space that Windows is taking up instead. I don't know. I wish I had a better answer for your issue.

---

### Post by rusty spork on 2011-10-24
Well, I just deleted my nuclear libraries (have the data on dvds), and I still can't log in.  Now there is ~20 GB of free space-so this most likely isn't a space problem.

---

