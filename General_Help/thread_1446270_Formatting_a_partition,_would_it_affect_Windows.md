---
title: "Formatting a partition, would it affect Windows"
date: 2010-04-03
forum: General Help
---

### Post by RJ12 on 2010-04-03
Ok so I have had Ubuntu 9.04 installed and I want to switch to 9.10, I know 10.04 will be out soon, but I like 9.10 because it just works. I know not to upgrade directly (Its always been a no-no). So I am gonna clean install Ubuntu 9.10. I want to get rid of 9.04 and give it to Ubuntu 9.10. But if I wipe that partition, will it affect Windows XP (I already put the MBR of Windows XP back using the fixmbr command.) I just have another concern, I have heard many people say that the new GRUB2 has trouble seeing Windows. I figured to go around that by using WUBI. I was hoping to format the ext3 partition with GParted to NTFS, mount it as a drive in Windows, and install to that "Drive". So what I need to know is, would Windows be affected by this formatting? And would GRUB2 (Maybe it got updated) see my Windows XP Partition and let me successfully boot into it?

Sorry for the long question, but I appreciate it! ;)

---

### Post by 2hot6ft2 on 2010-04-03
I for 1 have had no problems with grub or grub 2 (now called grub-pc) finding windows and letting me boot into it that includes win xp, vista and 7.

---

### Post by BrokeMahPC on 2010-04-03
Sorry if this doesn't exactly answer your question but I think you worry too much!
I use 9.10 and have tested the Beta of 10.04 and found that 10.04 works the same if not better in some respects than 9.10. it's very similar.
Never had a problem with Grub2 - initially people grumbled as it was different and they had to learn how to configure it all over again but read the guides and it's fine.
Wubi is good but dual booting with windows is even better. Remember that Wubi is occasionally sensitive to hard restarts / power failures  - a dual boot is far more resistant to this.
Don't fret, you don't even have to format, backup your windows data, home folder, save your bookmarks, addressbook and emails, just download 10.04 on April 29th / early May and use the manual install option to install it to your partition, a format is part of this process. It will not affect windows if the disk is already partitioned and you install it to the NON-windows partition. Read up on G-Parted (The partitioning tool) and the manual install / partitioning process, use ext-4, make your swap the size of your RAM. The mount point for the install needs to be / (root).
Take care - make sure you don't make silly mistakes and repartition / format the whole drive or wipe windows by accident. A little research and you will be fine - there are plenty of examples on the web.
Start here [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
It's a little out of date but there will be up to date documentation released with 10.04.
Windows 7 guide here from lifehacker - good guide and shows some of the steps you will need:
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

---

### Post by RJ12 on 2010-04-03
> **BrokeMahPC said:**
> Sorry if this doesn't exactly answer your question but I think you worry too much!
I use 9.10 and have tested the Beta of 10.04 and found that 10.04 works the same if not better in some respects than 9.10. it's very similar.
Never had a problem with Grub2 - initially people grumbled as it was different and they had to learn how to configure it all over again but read the guides and it's fine.
Wubi is good but dual booting with windows is even better. Remember that Wubi is occasionally sensitive to hard restarts / power failures  - a dual boot is far more resistant to this.
Don't fret, you don't even have to format, backup your windows data, home folder, save your bookmarks, addressbook and emails, just download 10.04 on April 29th / early May and use the manual install option to install it to your partition, a format is part of this process. It will not affect windows if the disk is already partitioned and you install it to the NON-windows partition. Read up on G-Parted (The partitioning tool) and the manual install / partitioning process, use ext-4, make your swap the size of your RAM. The mount point for the install needs to be / (root).
Take care - make sure you don't make silly mistakes and repartition / format the whole drive or wipe windows by accident. A little research and you will be fine - there are plenty of examples on the web.
Start here [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
It's a little out of date but there will be up to date documentation released with 10.04.
Windows 7 guide here from lifehacker - good guide and shows some of the steps you will need:
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

Ok, that answered most of my question. Here is what I think I need to do when I get to the partition part.
1. Click Manual
2. Select the ext3 partition and click "Change"
3. Click on the drop down that says "do not use this partition"
4. Change it to "EXT4 Journaled File System" (I think its worded like that)
5. Check "Format"
6. Move on (I will use Swap from old Ubuntu Install)

But now I what I need to know is, has the GRUB2 (Or grub-pc) problems where it does not see Windows or load Windows been ironed out / fixed. I think with any mistakes I could just restore the MBR from my XP CD, but I have heard that Windows won't recognize the hard drive. But it recognizes it when I had 9.04 on with the ext3 file system. I guess I'm not worried for my self, its for everyone else who uses this computer. It is my computer but my brother uses this to sync his iPod in iTunes with the music store (I will try to get my family to use the new Music Store canonical will be rolling out soon, if the prices are cheaper than the Music store with iTunes) he would kill me because, he wouldn't be able to get his apps.;)

Thanks!

Edit: I am logging off for the night

---

### Post by louieb on 2010-04-03
> **RJ12 said:**
> ...But now I what I need to know is, has the GRUB2 (Or grub-pc) problems where it does not see Windows or load Windows been ironed out / fixed.... 

Compaired to the old GRUB legacy - The os-prober in GRUB2  is much better at finding other operating systems. Fewer problems - much easier to fix.  

Usually to add another OS to the GRUB2 menu its as simple as running
```
sudo update-grub
```

---

### Post by BrokeMahPC on 2010-04-04
Steps 1-5 are correct - that should do it!
I don't think you will have problems with grub2 not seeing the windows partition - never had that problem.
(You can edit it to boot windows by default if thats the preference of your household BTW)
Windows will recognize the hard drive but it will not 'see' the ext4 file system or the swap. You will not be able to get into those partitions from 'My Computer' in windows. That is normal and a good thing from a security point of view. Windows XP only uses NTFS or Fat32. In future if you wanted to get rid of ubuntu (very unlikely!) you would have to use G-Parted to repartition/format those partitions back to NTFS.

You would still have Grub2 booting though - so to restore your windows boot loader - do the following:
For XP:
boot from a XP CD and, once the menu  loads, hit "R" to enter a command prompt.  Once there, choose which  partition you want, and enter an admin password (if you have one set).
then type  	Code:
 	fixmbr
fixboot 
 and the XP bootloader should be restored.

taken from:
[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

---

### Post by RJ12 on 2010-04-04
Ok, about to install. One last question. Will Ubuntu see the old swap and use it? or do I have to set it as a mount point as something?

---

### Post by neur0 on 2010-04-04
It should use it automatically, and it will be displayed that it's going to use it at some point during the installation, so no worry.

---

### Post by RJ12 on 2010-04-04
Man, you guys were right! I worry to much!! Thanks for helping through my dilemma. :)



*Solved*

RJ:p):P

---

