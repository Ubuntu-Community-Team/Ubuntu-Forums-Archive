---
title: "Reinstalling Grub"
date: 2010-10-26
forum: General Help
---

### Post by NPV1597 on 2010-10-26
Hi I am dual booting windows 7 and ubuntu 10.10

EDIT: I am booting ubuntu from a live disk on my flash drive

I had to reinstall windows, and I lost grub

I am following the instructions in this thread
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

but when i do /boot/grub/stage1 i get Error 15: file not found

Whats going wrong?

---

### Post by sebikul on 2010-10-26
You should look at this doc page: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Hope this helps!!

---

### Post by NPV1597 on 2010-10-26
> **sebikul said:**
> You should look at this doc page: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Hope this helps!!
It has the same directions as the other forum I linked. The problem is when I get to this step this happens

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

---

### Post by Quackers on 2010-10-26
If you are dual booting W7 and Ubuntu 10.10 (and it's not a wubi install) the guide you are following is too old.
10.10 used Grub2 not grub. I would suggest following this guide

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

If you have loaded parts of grub on to your system (by following the other guide) it may be better to follow the section of this guide regarding purging grub then re-installing grub2

---

### Post by wilee-nilee on 2010-10-26
If you run into trouble or you want to see your setup better run the bootscript in my signature. Feel free to post the text **in code tags** as described in my sig as well if you like.

---

### Post by katykat on 2010-10-26
I will also be facing this problem in the near future: Losing the grub2 sector on my primary Windows boot disk. 

All the solutions I've seen range from removing/reinstalling  Grub2 to installing lilo, and none of these seem acceptable. I have two linux drives and do not wish to risk mucking them up. 

Would it be possible to:
Remove all hard drives on the system. 
Install Win on sda
Install Lucid on a junk hard drive on sdb.
(the idea being here to simply get grub2 to write the boot sector to the windows drive)
Then remove the junk Lucid sdb drive.
And reinstall the normal Linux drive(s). 

The new windows drive would ideally have the grub2 bootsector. 
And a grub-2 update command should reconfigure the bootloader (if needed). 

Are there unintended consequences likely here??????

---

### Post by Quackers on 2010-10-27
katykat, please outline your present system and then give details of what you will be doing that would lose you the grub2 sector on your primary Windows boot disk.

---

