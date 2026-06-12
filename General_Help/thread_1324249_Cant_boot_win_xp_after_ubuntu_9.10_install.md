---
title: "Cant boot win xp after ubuntu 9.10 install"
date: 2009-11-12
forum: General Help
---

### Post by velardejose on 2009-11-12
Hi
I am using ubuntu in my home pcs and am very happy with it
I bought a toshiba nb200 netbook yesterday, and installed ubuntu 9.10 (full ver not remix) after resizing creating a D disk and a ext3+swap file partitions
Ubuntu 9.10 runs perfect (sound and network too)
Problem is when selecting win xp in grub the win loading screen apears and after 6-8 secs a blue screen flickers and the machine restarts
I can see the windows directory and all files from ubuntu
Thanks in advance

---

### Post by dragonboss on 2009-11-12
The blue screen could be BSOD (Blue Screen Of Death), meaning your windws could be broken and has nothing to do with ubuntu or grub since you saw the loading screen for windows.

---

### Post by Tiganjero on 2009-11-12
I agree with dragonboss. That is very likely.

George

---

### Post by wilee-nilee on 2009-11-12
> **velardejose said:**
> Hi
I am using ubuntu in my home pcs and am very happy with it
I bought a toshiba nb200 netbook yesterday, and installed ubuntu 9.10 (full ver not remix) after resizing creating a D disk and a ext3+swap file partitions
Ubuntu 9.10 runs perfect (sound and network too)
Problem is when selecting win xp in grub the win loading screen apears and after 6-8 secs a blue screen flickers and the machine restarts
I can see the windows directory and all files from ubuntu
Thanks in advance

Does grub show 2 loaders for XP if so one is a recovery which will over write/reinstall XP if you have nothing on there yet to save rewriting it may be an option it will leave grub intact. Do not do this though without confirming. On my net book it recovered a corrupted XP that came with my purchase. To confirm the partitioning install gparted in the Ubuntu from synaptic then open gparted and look at the partitions.

It sounds also that you repartitioned from XP I am not sure if this is part of the problem. Also when you say disc D is this a another hard drive or a partition.

---

### Post by velardejose on 2009-11-12
Thanks for your answers
Hope it is not a BSOD...
Yes when grub starts I can see 2 win partitions, one with xp home edition and the other (windows nt/2000/xp) seems to be the recovery file/disk, but when booting from there a box appears saying windows cannot find c \bin\erordialog.exe ... then another box says windows cannot find c \bin\bootpriority.exe and the machine rebots and the grub screen appears again
Is it possible to repair it?
Thanks in advance

---

### Post by wilee-nilee on 2009-11-12
> **velardejose said:**
> Thanks for your answers
Hope it is not a BSOD...
Yes when grub starts I can see 2 win partitions, one with xp home edition and the other (windows nt/2000/xp) seems to be the recovery file/disk, but when booting from there a box appears saying windows cannot find c \bin\erordialog.exe ... then another box says windows cannot find c \bin\bootpriority.exe and the machine rebots and the grub screen appears again
Is it possible to repair it?
Thanks in advance

Since it is a brand new computer I believe, if this is so you can get a recovery disc from the manufacturer or MS, or the actual XP DVD to do a fresh install and use they key on the tag that is on the computer. If at some point you can get the XP to boot hit the f8 key repeatedly to get to the safe mode and other options to see if something can be done there. I would also check the MS forums your computer is not the only one doing this, there are problems like this on stock no dual booting setups so you might get some help there. Also if this is a new purchase you have free access to the MS tech team find their # on line or PM me or email me and I will give you gthe support number, The # is available through the MS store by calling them. 

I think you have a fixable situation, but the key thing here is to follow a protocol that will protect you investment, and be the most efficient.

---

### Post by wilee-nilee on 2009-11-12
> **velardejose said:**
> Thanks for your answers
Hope it is not a BSOD...
Yes when grub starts I can see 2 win partitions, one with xp home edition and the other (windows nt/2000/xp) seems to be the recovery file/disk, but when booting from there a box appears saying windows cannot find c \bin\erordialog.exe ... then another box says windows cannot find c \bin\bootpriority.exe and the machine rebots and the grub screen appears again
Is it possible to repair it?
Thanks in advance

Since it is a brand new computer I believe, if this is so you can get a recovery disc from the manufacturer or MS, or the actual XP DVD to do a fresh install and use they key on the tag that is on the computer. If at some point you can get the XP to boot hit the f8 key repeatedly to get to the safe mode and other options to see if something can be done there. I would also check the MS forums your computer is not the only one doing this, there are problems like this on stock no dual booting setups so you might get some help there. Also if this is a new purchase you have free access to the MS tech team find their # on line or PM me or email me and I will give you gthe support number, The # is available through the MS store by calling them. 

I think you have a fixable situation, but the key thing here is to follow a protocol that will protect you investment, and be the most efficient.

With any fresh install, dual boot, or repartitioning with MS you want to boot the windows to let it do the auto disc check on resizing, and defrag before you install a second OS. Toshiba I am sure has a live down load of the recovery image so that this sort of situation can be fixed by you rather then having the computer returned. I would call Toshiba and see what your options are as well. The forum seems like a quick fix but it could be the wrong fix just as easily, and leave you stranded.

---

