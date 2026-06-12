---
title: "Grub Issues"
date: 2010-01-02
forum: General Help
---

### Post by popanik on 2010-01-02
Hallo everyone :)
On my PC i have 2 hard discs . One has an Ubuntu 9.10 installation and on the other i have recently installed Windows 7.
As I expected I can't boot Ubuntu, because I need to restore Grub 2 . The thing is, I searched the forum for similar issues, and i tried some of them, but the problem still remains...
Is it because I have two hard discs?If not, which is the best way to fix this problem?
Thank you

---

### Post by Leppie on 2010-01-02
how did you do the installations? did you first install windows on the first disk and then set the 2nd disk to boot 1st in your pc's bios and then installed ubuntu onto that disk?

or did you install ubuntu on the 2nd disk (the non bootable one) first and then installed windows on the first disk (the bootable one)?

---

### Post by popanik on 2010-01-09
> **Leppie said:**
> how did you do the installations? did you first install windows on the first disk and then set the 2nd disk to boot 1st in your pc's bios and then installed ubuntu onto that disk?

or did you install ubuntu on the 2nd disk (the non bootable one) first and then installed windows on the first disk (the bootable one)?

I installed ubuntu on the 2nd disk (the non bootable) first and then windows on the first disk(which boots...) . 
The thing is, i haven't touch BIOS for Master/Slave configurations because I don't think it's necessary . 

P.S.: Sorry for the delayed answer :(

---

### Post by Leppie on 2010-01-09
then set the 2nd drive as 1st boot device in the bios, this should boot you into ubuntu.
then issue the following commands in a terminal:
```
sudo grub-install /dev/sdb
sudo update-grub
```

this should add win7 to the grub menu.

---

### Post by popanik on 2010-01-10
> **Leppie said:**
> then set the 2nd drive as 1st boot device in the bios, this should boot you into ubuntu.
then issue the following commands in a terminal:
```
sudo grub-install /dev/sdb
sudo update-grub
```

this should add win7 to the grub menu.

Thanks mate :D
Solved the issue :D

---

