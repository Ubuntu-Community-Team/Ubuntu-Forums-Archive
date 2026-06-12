---
title: "am i able to install Ubuntu in this situation ?"
date: 2011-04-17
forum: General Help
---

### Post by ozthecoz on 2011-04-17
Hi,

First question really is, in the following situation can i install ubuntu ?

Advent Verona Laptop running Windows7
Problem with the win 7 and now it will only let me boot to the system recovery partition - unfortunatly, no matter what i do i cannot get anything in the system recovery to work - laptop just hangs or reboots to the same point.

So i thought lets give ubuntu a try......

Downloaded 10.10 from here:[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) and then followed the instructions on that page to put the iso file onto a usb pen drive - all seemed to go ok untill i came to put it on my advent laptop - and i get the kernel_thread_helper+0x6/0x10 problem.

had a google and found out about changing APCS=no etc but when ever i try to change anything in the F6 boot bit i get a could not find kernel image message and instalation carries on, again stalling at the kernel thread helper message.

Any ideas ? Am i trying to do the impossible ?

Cheers in advance

---

### Post by TeoBigusGeekus on 2011-04-17
Try with the alternate cd:
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download")

---

### Post by ozthecoz on 2011-04-17
> **TeoBigusGeekus said:**
> Try with the alternate cd:
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download")

Cheers, i have downloaded and tried that and get a little further but now the problem seems to be the following error message :

ubuntu cannot read removable media

so again , installation stalls and i cant get any further :(

---

### Post by aerofly5 on 2011-04-17
so, if I understand correctly, there is no way to get into safemode? If you are able to get into safemode, try doing a wubi install

---

### Post by ozthecoz on 2011-04-17
yeo at the mo there is no way of getting into safe mode - and with it being a new=tbook there are no instalation disks - all the recovery rubbish is on a partition and wont ruddy respond 

Ifi can get ubuntu working i'll be sticking it on all my PCs and never giving Gates another sheckle !!!

---

### Post by 3rdalbum on 2011-04-17
Are you sure it's not a hardware problem? If Windows isn't working, and your recovery partition isn't working, and Ubuntu isn't working... then it's possible that those problems are linked.

You could try downloading Ubuntu 11.04, which is in beta at the moment (but only a few days out from final release). If it's not a hardware problem and instead it's an incompatibility problem, then the newer kernel in Ubuntu 11.04 could fix the problem.

I'd also check that your CPU isn't overclocked, which is less likely on a laptop, but worth checking in your BIOS.

---

