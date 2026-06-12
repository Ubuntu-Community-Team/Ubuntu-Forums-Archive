---
title: "VBOX Setup Location &amp; Memory Settings?"
date: 2010-01-05
forum: General Help
---

### Post by sandman3838 on 2010-01-05
Hello

I have a few questions about VBOX.

My system now is a dual boot computer with Ubuntu and Winxp each on there own HD.  The system has 4gb memory with a 512mb Nvidia video card.

1.  If I understand it correctly, VBOX installs it's own copy of Windows to a directory.  I can't piont it to the Winxp that I already have installed on the other HD?  

2.  VBOX has a two sliders for Memory, one for System and the other for Video.  Do any of you have a system such as mine and would you have any suggestions for the two sliders settings?

Thank you for your time and help.

Sincerely

---

### Post by SecretCode on 2010-01-05
*VBOX installs it's own copy of Windows to a directory*
Not quite - vbox gives you a virtual machine with a virtual hard disk which is held in a single file, of .vdi type. Then you (not it!) install windows onto that virtual hard disk. So it's not a directory and can't be accessed by the host system, but essentially you are right.

There is a way, with VirtualBox, of creating a virtual machine that uses a separate, physical disk, so you could run your physical XP system as a 'guest' while you have booted Ubuntu. However
(a) it's complicated to set up (I have not done it myself)
and (b) Windows will see a hardware change and require reactivating with Microsoft - every time you reboot as virtual after a physical boot, and vice versa.

That said, a lot of people use it successfully. You should do some reading - e.g. google for "physical to virtual", and browse forums.virtualbox.org.

*VBOX has a two sliders for Memory, one for System and the other for Video. Do any of you have a system such as mine and would you have any suggestions for the two sliders settings?*

I only have 2GB so I keep the system RAM just under 1GB - 700MB to 900MB. And the guests run fine. You might want to allow 1.5GB ... unless you plan to run more than 1 at a time, in which case reduce the amount for each.

I always set 64MB of video RAM.

---

### Post by sandman3838 on 2010-01-05
Thanks for the advice and info I'll be sure and use it!

Thank you.

NEW INFO
I just noticed that I guess that there are two versions?
one is in the Ubuntu Software Center

the other is here:
[http://www.virtualbox.org/](http://www.virtualbox.org/)

Is one better that the other?

---

### Post by SecretCode on 2010-01-06
In general, things in the Ubuntu Software Center are likely to be a release or two older than the latest version you can get directly from the supplier, because it takes time to package and load it.

Additionally, there are two versions of VirtualBox available from Sun - PUEL - "private use and evaluation licence", and OSE - "open source edition". They're the same but for some features - in particular, USB support is only in the PUEL version.

Because of Ubuntu's policies, only the OSE version is included in the repositories. The latest version in the repo of virtualbox-ose is 3.0.8-dfsg-1ubuntu1. But Sun supplies the source code for version 3.1.2.

The PUEL licence is valid for most uses, even personal use at work, so that's the one to go for. See section "Debian-based Linux distributions" at [Linux_Downloads - VirtualBox](http://www.virtualbox.org/wiki/Linux_Downloads).

---

