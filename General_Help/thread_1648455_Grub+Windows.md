---
title: "Grub+Windows"
date: 2010-12-18
forum: General Help
---

### Post by ionbasa on 2010-12-18
okay, so after i managed to install ubunut x64 my Windows 7 will not load...

my partition table looks like this:
Partition          File System          size
/dev/sda1          ntfs                 100.00 MiB
/dev/sda2          ntfs                 445.66 GiB
/dev/sda3          extended             20.00  GiB
  /dev/sda5        ext4                 19.12  GiB
  /dev/sda6        unknown(swap?)       895.00 MiB
unallocated        unallocated          1.02   MiB

currently I was using GParted to find this out. I think the Grub boot loader is pointing to the wrong partition for windows. This is because a few months back I had an uncessesful atempt to install ubuntu w/o grub and tried to use the windows boot loader.:shock:

I then realized that it did not work, so I was able to fix it using My Windows 7 recovery tools. 

So in Grub should it be pointing to /dev/sda1 for windows or /dev/sda2 ?

please note that i have never edited Grub boot loader so help will be necessary.

---

### Post by Quackers on 2010-12-18
Is the Windows loader appearing in grub? If so what does it say?

---

### Post by ionbasa on 2010-12-18
Yes it does apear. Let me restart and let you know!
EDIT: I have 2 loaders:
Windows 7 (loader) (on /dev/sda1)
Windows 7 (loader) (0n /dev/sda2)

---

### Post by ionbasa on 2010-12-18
so when using /dev/sda2 it will boot okay, but when using /dev/sda1 it will not. I know that windows is set up to use the /dev/sda1 boot loader by default. That is the one I messed up earlier.

---

### Post by Quackers on 2010-12-18
sda1 is just a boot partition. If you use the one that refers to sda2 you should have no problem booting Windows.
If you are happy, please mark the thread as solve, using the Thread Tools near the top of the page. Thanks.

---

### Post by ionbasa on 2010-12-18
okay, but is there any way I can remove /dev/sda1 from Grub?

---

### Post by Quackers on 2010-12-18
> **ionbasa said:**
> okay, but is there any way I can remove /dev/sda1 from Grub?

Yes, but you may decide to leave it :-)
Have a look through this guide by drs305 on the editing of grub titles

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by ionbasa on 2010-12-18
wouldn't I be able to comment it out:
[http://ubuntuforums.org/showthread.php?t=94075](http://ubuntuforums.org/showthread.php?t=94075)

---

### Post by Quackers on 2010-12-18
From where? The grub menu? No.
You need to edit the appropriate file as shown in the guide I linked to.

---

### Post by ionbasa on 2010-12-18
okay, I managed to take out the recovery partition from Grub....Good thing i know some C++ lol.

Also thank you for the help you provided.

---

