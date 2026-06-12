---
title: "Uninstalled Ubuntu still on Boot Menu"
date: 2010-01-22
forum: General Help
---

### Post by rob22941 on 2010-01-22
Ok I ran into some issues with Ubuntu and had to reinstall, after the third time it worked. BUT, now I have 4 Ubuntu's listed on my Boot Menu and for the life of me I can't figure out how to delete the dead ones. I was under the impression by uninstalling them they would disappear and they didn't. I only want my Windows 7 and Ubuntu listed. Any ideas?

---

### Post by ajgreeny on 2010-01-22
Are you sure you installed over the first ubuntu install and not alongside it?  If you allowed ubuntu to install by the default method, you will still have the original and new versions on disk.

Show us the output of ```
sudo fdisk -l
``` and we can try to put you right.

---

### Post by n0dix on 2010-01-22
Did you see the menu.lst?? 
```
sudo gedit /boot/grub/menu.lst
```
Post it.

---

### Post by 73ckn797 on 2010-01-22
> **n0dix said:**
> Did you see the menu.lst?? 
```
sudo gedit /boot/grub/menu.lst
```Post it.


This will not work with 9.10.

ajgreeny has the first step needed.

---

### Post by ranch hand on 2010-01-23
> **ajgreeny said:**
> Are you sure you installed over the first ubuntu install and not alongside it?  If you allowed ubuntu to install by the efault method, you will still have the original and new versions on disk.

Show us the output of ```
sudo fdisk -l
``` and we can try to put you right.
I bet you have it right.

---

### Post by rob22941 on 2010-01-23
> **ajgreeny said:**
> Are you sure you installed over the first ubuntu install and not alongside it?  If you allowed ubuntu to install by the efault method, you will still have the original and new versions on disk.

Show us the output of ```
sudo fdisk -l
``` and we can try to put you right.

robert@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23112a04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       91202   732469248    7  HPFS/NTFS
robert@ubuntu:~$


I was trying to get 8.04lts installed but it just wouldn't install. So I ended up just doing 9.1. It looks like it installed along side it but I'm not sure how to now erase the old installs. Thanks for your help!

---

### Post by ranch hand on 2010-01-23
Is that the complete out put from fdisk -l?  i do not see an Ubuntu partition there.

How about running this script and post all the resulting text that will be generated on your desktop.  You ca nrun this from the live cd if needed;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by rob22941 on 2010-01-24
> **ranch hand said:**
> Is that the complete out put from fdisk -l?  i do not see an Ubuntu partition there.

How about running this script and post all the resulting text that will be generated on your desktop.  You ca nrun this from the live cd if needed;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Sorry for the delayed response. Yep that was everything. Here is the RESULTS.txt output file. Hope this is the right info!

---

### Post by oldfred on 2010-01-24
You have Wubi installed in your NTFS partition for windows. Wubi is ok for trying Ubuntu as it is a full install but is running on the windows partition, so any issues with windows will also cause issues with Wubi.

You show two kernels (and their recovery). We recommend that you keep at least two kernels, so if there is an issue with one you can still use the older one.

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
The Windows-based Ubuntu Installer (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows. It lets a Microsoft Windows user try Ubuntu without risking any data loss due to disk formatting or partitioning.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
Wubi is an officially supported Ubuntu installer for Windows users that can install and uninstall Ubuntu as any other Windows application, in a simple and safe way.

---

### Post by ranch hand on 2010-01-24
What you have there is normal and correct.

You have, first, the entry to boot to the current kernel.  Then recovery mode to the current kernel.

The other 2 entries are the same thing to the same OS but for the old kernel that was in use before you updated after installation.  If they bother you they can be removed in synaptic.  A lot of folks like to keep an old kernel around in case the new one doesn't boot (Alphas are fun).

---

### Post by rob22941 on 2010-01-24
Would it be in my best interest to install Ubuntu onto a separate partition with no reliance on Windows?

---

### Post by rob22941 on 2010-01-24
> **oldfred said:**
> You have Wubi installed in your NTFS partition for windows. Wubi is ok for trying Ubuntu as it is a full install but is running on the windows partition, so any issues with windows will also cause issues with Wubi.

You show two kernels (and their recovery). We recommend that you keep at least two kernels, so if there is an issue with one you can still use the older one.

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
The Windows-based Ubuntu Installer (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows. It lets a Microsoft Windows user try Ubuntu without risking any data loss due to disk formatting or partitioning.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
Wubi is an officially supported Ubuntu installer for Windows users that can install and uninstall Ubuntu as any other Windows application, in a simple and safe way.

When I first attempted to uninstall Ubuntu I ran the uninstall feature in Wubi. I don't believe it uninstalled anything, because now on my boot menu I have:
Windows 7
Ubuntu
Ubuntu
However one Ubuntu works and the other doesn't. Is there a way to completely remove both (all) Ubuntu or Wubi installed versions and start from scratch again with Ubuntu on a separate partition from Windows?

---

### Post by oldfred on 2010-01-24
We like to recommend that if you are beyond the test it/try it stage. It dual boots normally well with windows, but you do have to shrink your windows partition and make space for Ubuntu to add new partitions.

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

Be sure to use the windows tools to shrink the windows partition and reboot several times to make sure windows is happy with the size change before installing Ubuntu into the space you create.

---

### Post by rob22941 on 2010-01-24
> **oldfred said:**
> We like to recommend that if you are beyond the test it/try it stage. It dual boots normally well with windows, but you do have to shrink your windows partition and make space for Ubuntu to add new partitions.

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

Be sure to use the windows tools to shrink the windows partition and reboot several times to make sure windows is happy with the size change before installing Ubuntu into the space you create.

Ok, I think I have enough information to do what I want to do much thanks to everyone! I'm going to experiment with one of my older computers, rather then my primary unit I use for school purposes. Last thing I need is this unit to go down. Thanks again!

---

### Post by ranch hand on 2010-01-24
It is a good idea to be real careful with an alpha release.  I am on my main box but the internal drives are turned off in bios and I am running on an external enclosure (dual sata with two 320Gb drives and 12 OS').

I have no experience with wubi but see no sense in putting a good, secure OS inside a piece of crap.  Seems weird to me.

---

### Post by rob22941 on 2010-01-24
Alright I got Hardy Heron 8.04lts installed correctly now. I still have it installed using Wubi. However once I have some more time to spend reading up on installing it either on a separate partition or onto a secondary drive I'm going to do so. I'm just pretty darn busy starting the Spring semester. Thanks again for your help.

---

