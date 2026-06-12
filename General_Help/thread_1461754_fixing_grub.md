---
title: "fixing grub"
date: 2010-04-24
forum: General Help
---

### Post by wcutrombonekid on 2010-04-24
so, i moved my windows partition on my hard drive.  what do i have to do now to update grub so that it will boot to it?

---

### Post by mikewhatever on 2010-04-24
Try running **sudo update-grub** ...

By the way, why fix grub? It's not broken.

---

### Post by wcutrombonekid on 2010-04-24
> **mikewhatever said:**
> Try running **sudo update-grub** ...

By the way, why fix grub? It's not broken.

you're right, i'm the one that messed with it.
I tried that and it didn't work, i really don't know a lot about grub and didn't think about it when I did that

---

### Post by oldfred on 2010-04-24
To mikewhatever point, it is probably not grub that is the issue. Windows does not like moving. 

You may have to install the windows boot loader and see if windows boots. Then when it does not run the windows repairs. 
boot.ini will be wrong:
[http://support.microsoft.com/kb/314477](http://support.microsoft.com/kb/314477)

Grub will only boot working windows. Once windows works reinstall grub.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by wcutrombonekid on 2010-04-24
ooookkkkkaaaayyyyyyy
i figured it out

i deleted windows

haha

not a big deal, there was nothing sensative on there, it was simply there if i needed it.

so basically what i have left is a 25 GB partition with ubuntu on it and a blank 320 GB HD


haha

this makes me laugh because its my fault.
anyway, can anyone direct me to an article on reinstalling windows on a partition, i've already got one set up, can I just use the recovery CD on it, or will it try and take over the whole disk

---

### Post by oldfred on 2010-04-24
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

Older instructions may be about reinstalling grub legacy after windows is installed. IF you have grub2 with Karmic or later then you need the instructions for reinstalling grub2.

---

