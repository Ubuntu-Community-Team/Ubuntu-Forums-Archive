---
title: "Don't know what to do"
date: 2010-01-31
forum: General Help
---

### Post by Zielvos on 2010-01-31
I have never had a problem trying to install ubuntu on a system and have tried everything that I can think of. I have tried to install 9.10 in 32 bit and in 64 bit and still can't get it installed. It will freeze during setup and if I'm lucky it will freeze after i get to the desktop. 

I did get the 32bit to install but it just froze within minutes of just hanging out on the desktop. As for the 64bit, it loads everything but the background and it will freeze. 

Info on the computer
Compaq Presario SR5210NX
Intel Celeron 420
Old os was Vista home Premium 

Also this is one of those POS that you can get at Best Buy, they kept all the disks so there is no turning back unless I want to pay them to put vista back on it. 

Thanks in advance.

---

### Post by Swagman on 2010-01-31
Sounds like a bad stick of RAM mate.  I've had that issue.

---

### Post by Zielvos on 2010-01-31
That could be but got XP on it to test some stuff out and its just fine.

---

### Post by Swagman on 2010-01-31
Frustratingly that also happened to me.

---

### Post by NightwishFan on 2010-01-31
Not every machine is entirely compatible with Ubuntu. It may take a bit of tweaking to get it working right. (Though usually not.)

I am sorry to say I cannot help more full right now, but If you do not find any solutions, I will be free to help you later today.

---

### Post by chewearn on 2010-01-31
Sorry if you have verified the followings, but it's good to get the basics out of the way first.

1. have you run the live CD disc verify option?
The disc could be good, but maybe the combination of disc and the CD-ROM of that particular PC is not good.

2. have you run the memtest from the live CD?
You mentioned WinXP is working fine on the PC.  And probably there is nothing wrong with the PC memory.  But running memtest will definitely put this matter to rest.

---

### Post by john newbuntu on 2010-01-31
Few more things I can throw here are:
Anything suspicious in the logs (/var/log) when it happens to boot?
Is the disk ok? If installation completes, can you verify from a liveCD using e2fsck?
If you happen to get into the system, run htop and sort by cpu% (and later perhaps even by mem%). See if can find the culprit.
Any fancy graphics cards on the system?

---

### Post by spiky001 on 2010-01-31
Just to add were the discs burned at a slow speed?

---

### Post by gradinaruvasile on 2010-01-31
XP is not that sensitive to bad RAM as Linux or Windows 7 (maybe Vista too) for that matter. Ive seen computers run with XP and dont boot with Ubuntu because of bad RAM.

---

### Post by jcampen on 2010-01-31
I have had the same problems before and was usually from cheep quality cd/dvds or the ISO hash sum didnt add up, so was a bad down load. Always do the hash check of the ISO before bothering to burn it to disk. 
How I figured it was the cd quility and burning, I test instaled it from the drive I had downlaoded the ISO to and insalled it on VirtualBox and the instaltion was fine, so meant a good ISO
Some good advise already on here, and do select a slow burning speed for the CD.

---

### Post by Zielvos on 2010-02-01
Thanks for the tips and everything else guys. Sadly its still not working but going to try a few other things. Because windows can still be installed I will put that on there and just try that weird installer thing.

This is the last thing I try before I just tell my sister to get a new computer because she was thinking of getting a new laptop anyway.

---

