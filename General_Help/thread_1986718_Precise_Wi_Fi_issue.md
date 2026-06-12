---
title: "Precise Wi Fi issue"
date: 2012-05-25
forum: General Help
---

### Post by swright007 on 2012-05-25
I really enjoy running Ubuntu on my home computer and my Windows on my Toshiba Satellite laptop recently crashed.   I tried Ubuntu on it, Precise, and it worked wonderfully except that it has issues with my Wi Fi at work.   I can go to download something and it says it will take like 10 hours to download.   If I boot up under another Linux based distro (I've tried Mageia and Linux Mint so far) it would say more like an hour if I tried to download the file the exact same way.  (yes, I am referring to Linux .ISO images as the large file being downloaded :)  ) 

I am in hopes that there is a solution or a package one can point me to as Mint MATE is based directly off Ubuntu and it works well there.   I prefer Ubuntu and would love to stay with this for my end all computer solution.   Thank you in advance.

                                                 Scott Wright

---

### Post by wildmanne39 on 2012-05-26
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

