---
title: "Get rid of grub"
date: 2010-02-17
forum: General Help
---

### Post by keth802 on 2010-02-17
I installed ubuntu 9.10 on a hard drive that I no longer use, however, I cannot boot my computer without it in. How do I solve this problem? Should I just completely uninstall?

---

### Post by ankspo71 on 2010-02-17
Hi,
Before you attempt this, could you clarify which operating system you would like to boot? If you don't want to use ubuntu, then my advice won't help. (sorry)

original message:
You can use that extra drive for storage, but if you would like to have it out you can use the following commands.

First, leave the other hard drive in the computer. Now start up Ubuntu. I'm not sure where your grub is installed now, but I am assuming it is on hard drive sda (the first hard drive).

Next run these commands in the terminal:
```
sudo update-grub
```then
```
sudo grub-install /dev/sdb
```These commands will update grub and install it to the second drive.
If all worked out as hoped, you should be able to shutdown, remove the other drive, and be able to boot back into ubuntu again. If not, you might have to install grub to sda etc.

here is a guide for more reference
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by Arand on 2010-02-17
First of all, what is it you're trying to boot at the momemt, windows or ubuntu?

---

### Post by DrMelon on 2010-02-17
I know what he's done. I made the same mistake a while ago - I installed Ubuntu on an External HDD, but I couldn't boot without it in - since Grub would give me errors.

If he has a windows install, we should point him to the "restore MBR" advice.

---

### Post by keth802 on 2010-02-17
I want to boot windows 7. I installed 9.10 on an external drive and now I can't boot without it plugged in. Also, I have another partition on my internal drive with a second installation of 9.10, that I want to keep.

---

### Post by oldfred on 2010-02-17
If you boot win7 you will not be able to boot Ubuntu. You need to have the grub for the external installed on the external so if in BIOS it boots first it will load that grub and grub from the 9.10 internal installed to sda the internal drive. The grub will find your win7 install and allow you to choose which to boot.

To give specific instructions run this script so we know exactly where everything is.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

if you can boot into boot copies of Ubuntu with the external installed you should be able to boot each and reinstall grub from each, being sure to select the correct drive to reinstall to:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

ankspo71 instructions will work if you boot from the external and to reinstall grub to the external if it is sdb. Similar instructions if you boot from the internal install except install grub to sda.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Arand on 2010-02-17
I am guessing that your mode of installing was:
1. win7 on internal
2. ubu on internal
3. ubu on external

If this is the case, and you installed grub automatically each time without any advanced settings, most likely it's a simple matter of overwriting the master boot record (MBR) on your internal drive.

The MBR would currently would point towards starting grub from the external drive, and we need to make it instead load grub from the internal drive.

For that end the instructions given above should suffice, start the internal ubuntu and follow the instructions.
Make sure that the "/dev/sdXY" part of the command is the number for the _internal_ ubuntu install partition, and similarly that the "/dev/sdX" part is the number for the internal drive ("X" will be the same in this case).

- Arand

---

