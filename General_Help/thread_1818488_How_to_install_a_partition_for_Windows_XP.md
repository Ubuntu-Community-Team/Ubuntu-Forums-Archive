---
title: "How to install a partition for Windows XP"
date: 2011-08-04
forum: General Help
---

### Post by SteezMcGee420 on 2011-08-04
Hello, I am somewhat new to Linux, and I am not very experienced at all with handling hard drives and partitions. I currently have a normal install of Ubuntu 11.04 running just fine, but I am looking to play some games on steam. While I am aware that it is possible to run Steam under ubuntu, through wine, I know that the performance will not be optimum, and I need that, as I have a poor computer. I am looking for simple, step-by-step instructions on how to create a sized partition for Windows, install Windows, and then clean things up, and make sure everything, including my GRUB, and MBR (Note: I do not know much about either of these things) Are all in order. If you could help me out with my problem, I would very much appreciate it.

---

### Post by SteezMcGee420 on 2011-08-04
Shameless first self-bump

---

### Post by purple_sticky_punch on 2011-08-04
wow i have this same exact question except my computer is average performance and i havent installed ubuntu yet because i want to make shure i can still play all my steam games on the os. also if any1 has any info on emulators (nintendo 64, nintendo ds, dreamcast) running on ubuntu that would be great too.

---

### Post by justinjthomas on 2011-08-04
Go to System -> Administration -> Disk Utility

Select your Hard drive from there. It is just like disk utility in windows.

Select a partition in which you're about to install windows.

Format it with NTFS file system not any other.

Your drive is ready go ahead with that bootable XP.

You may need to re-install Grub after XP installation. Let me know by replying here if you encounter any problems

---

### Post by purple_sticky_punch on 2011-08-04
tyvm i have to try this after my gf goes to bed tonight ill let you know how it went thank you again.

---

### Post by SteezMcGee420 on 2011-08-04
> **justinjthomas said:**
> Go to System -> Administration -> Disk Utility

Select your Hard drive from there. It is just like disk utility in windows.

Select a partition in which you're about to install windows.

Format it with NTFS file system not any other.

Your drive is ready go ahead with that bootable XP.

You may need to re-install Grub after XP installation. Let me know by replying here if you encounter any problems


Thank you for helping. My current dillemma right now is not knowing how to create a new partition of my main hard drive. Using disk utility, I select my hard drive, click 'format hard drive', and it brings me a window on formatting it, and selecting the format and the label. Should I label it as whatever, (i.e. "Windows Partition"), select NTFS from the drop down menu, and then click continue until it fully creates the new partition? My only concern is that I will somehow do this wrong, and delete data that is currently stored on the drive. 

P.S., What would re-installing GRUB do, and how complicated would that process be?

---

### Post by SteezMcGee420 on 2011-08-04
Also, once I have made that partition, how would I boot and install Windows XP? Would I do it the same way I would normally go about doing it when wiping a hard drive, except select the partition I created? Also, how will I know which partition is the correct one? Once again, thank you for your help.

---

### Post by justinjthomas on 2011-08-04
Please specify sizes of your partitions.
If you haven't partitioned your HDD yet then you must do it before installing multiple operating Systems.

Before formatting any of the partitions make sure you backup your data to some other partition. 

Grub2 Reinstall is not so complicated. 

Don't worry it is just the re-installation of your boot loader.

Reply The progress.

---

### Post by Basher101 on 2011-08-04
There is a whole thread about how to restore your grub2, just use the search

---

### Post by oldfred on 2011-08-04
Make sure the NTFS partition you create is a primary partition - sda1 thru sda4. Windows only installs first time to a primary partition as that is all it can boot from. You also need to put the boot flag (active partition in windows) on that primary partition for windows to see it.

Info on reinstalling grub2's boot loader to the MBR.
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by SteezMcGee420 on 2011-08-05
Thank you all very much for your help. I haven't gone ahead and done these steps yet, as I have to get a good night's rest. However, I will be trying this again in the morning, and I will report then.

---

