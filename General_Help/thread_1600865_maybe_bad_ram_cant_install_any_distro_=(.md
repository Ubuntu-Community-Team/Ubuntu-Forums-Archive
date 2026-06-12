---
title: "maybe bad ram? cant install any distro =("
date: 2010-10-19
forum: General Help
---

### Post by cain071546 on 2010-10-19
my names IAN I'm a Ubuntu and Debian user 
i have a hp desktop I'm working on
P4 2.6ghz 2gigs DDR333 80gig wester digital
Nvidia Geforce 7600gs 350watt P/supply in a BIG OLD custom asus case plus LED fans so no overheating issues =)

 [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00026876&lc=en&dlc=en&cc=us&product=341288](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00026876&lc=en&dlc=en&cc=us&product=341288) 
i have tried and failed to install pretty much everything in my dvd case Ubuntu 10.04+10.1 and Mint both Debian and Deb-net install
fedora 13 openSUSE 10 nothing worked ALL RANDOMLY crash or freeze during the file transfer/installation and i mean RANDOM
i have been unable to produce the same results twice.
i did as expected i searched Google and trouble shooted
and all i can think of is bad ram so i ran memtest86
by pass 5 i had over 1000 errors
have i found my bottle neck??
is it common to have so many that errors with the ram test
Windows 7 seems to be the only thing that will load
wye will shitty windows install and run fine NO lag when i cant get anything thing else passed a file transfer??

oh and has a new hard drive/thats not the issue.
i first posted this in the Debian forums but after failing to get Ubuntu to run either i came to the friendly local forum 

thanx guys

---

### Post by plucky on 2010-10-19
> and all i can think of is bad ram so i ran memtest86
by pass 5 i had over 1000 errors
have i found my bottle neck??

Any errors in MEMTEST is a no no.
If you have more than one stick,just run one at a time and see which one has the problem.
If you only have one stick,you will have to replace it.
> Windows 7 seems to be the only thing that will load
Windows and Linux handle memory in different ways.

Good Luck

---

### Post by ivarn on 2010-10-19
Here's an idea. Install xubuntu for now and go buy a better/greater memory card.
Then, upgrade the xubuntu packages to regular ubuntu.

---

### Post by P4man on 2010-10-19
memtest produces ZERO errors if you dont have a defect module (or ram/motherboard compatibility issue).  If you get hundreds, then clearly you found the problem. That windows still loads and appears stable doesnt prove anything; some OS's load top down, others bottom up (from beginning or end of ram). The faulty chip could also happen to be mapped in windows for some process you dont use.

---

