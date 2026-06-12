---
title: "Gparted Not Showing Partition?"
date: 2011-06-07
forum: General Help
---

### Post by Anson S on 2011-06-07
First of all, let me say I'm a brand new Ubuntu user. I've almost run out of space on the Ubuntu partition, so I figured I would re-size it using Gparted. However, Gparted is not showing that I have any partition in the main hard disk. What's going on?:confused:
Thanks for any help!

---

### Post by mike555 on 2011-06-07
I think you mean that gparted only shows one ,right? if that one is ntfs, then you must have installed Ubuntu using "Wubi" installer to install Ubuntu inside Windows ....... I don't think you can change it's size ....
   You should do a real install to a separate partition, sizing it as you want, there are lots of instructions online ...  if you need more help post back ...

---

### Post by Anson S on 2011-06-07
Thanks Mike, yes I did use Wubi to install it. So, there is no partition because it's just in the windows partition?

---

### Post by oldfred on 2011-06-07
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
The Windows-based Ubuntu Installer (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows. It lets a Microsoft Windows user try Ubuntu without risking any data loss due to disk formatting or partitioning.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by Anson S on 2011-06-07
Thanks for the info guys! I guess I'll be moving ubuntu to a partitioned section on an external hard-drive now.

---

### Post by mike555 on 2011-06-07
Be careful, where you install Grub to , if you always have the external plugged in it might not matter as much , but if you install grub to the MBR grub might not let you boot if the external isn't plugged in............. in a case where you might not want the external always plugged in then install grub to the external and use a different bootloader to boot it (Chain loading).

 I use GAG bootloader ; [http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

### Post by Anson S on 2011-06-07
Thanks again Mike, though now I'm having a different problem. Gparted won't show the external drive, so I can't partition and format it. I may just want to start a new thread for that, but figured I'd ask here first. I did google the problem, but the answers from here didn't solve it.

---

### Post by oldfred on 2011-06-07
Post these, perhaps a partition issue? Change sdb if not external not sdb.

sudo parted /dev/sdb unit s print
sudo fdisk -lu

---

### Post by Anson S on 2011-06-08
> **oldfred said:**
> Post these, perhaps a partition issue? Change sdb if not external not sdb.

sudo parted /dev/sdb unit s print
sudo fdisk -lu

When I enter "sudo parted /dev/sdb unit s print" I get:
 ```
Error: Could not stat device /dev/sdb - No such file or directory. 
```

And when I enter "sudo fdisk -lu" I get:
```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156232124    78116031    7  HPFS/NTFS
```

---

### Post by Anson S on 2011-06-08
> **oldfred said:**
>  Change sdb if not external not sdb.

Clarification please?

---

### Post by oldfred on 2011-06-08
You just posted info on internal sda formated NTFS. I thought the issue was with the external drive or sdb?

The fdisk is showing you do not have external plugged in. And of course then parted could not find sdb.

---

### Post by Anson S on 2011-06-08
> **oldfred said:**
> You just posted info on internal sda formated NTFS. I thought the issue was with the external drive or sdb?
Yes the problem is with an external drive. I just followed what you told my to enter in the terminal. As I said, I'm new to ubuntu and don't know much as of yet. How do I check the external drive?

> **oldfred said:**
> 
The fdisk is showing you do not have external plugged in. And of course then parted could not find sdb.
The external drive it plugged in, I just checked it. For some reason, Gparted isn't seeing it, and that's my problem.

---

### Post by linuxinstalledfromhdd on 2011-06-08
Just a quick observation.  Since you installed Wubi and you are running out of space, maybe it would be a good time at this point maybe, to download an Ubuntu ISO and burn that to a disc or create a Live Flash Drive of Ubuntu?  

If the only thing you have installed on your computer at the moment is just Windows, an Ubuntu installation disc will resize that parition and install Ubuntu side-by-side.  While it is installing you can disconnect your external drive until you have Ubuntu fully installed on it's own partition on your hard drive, and then you can hook up your external USB drive after it's done with the Ubuntu installation, and it will find it. :) 

Here is where you can get the iso and instructions on how to burn that to a disc or Flash Drive:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Sometimes it makes more sense to install Ubuntu to it's own dedicated partition, and save the user time and hassle.

---

### Post by mike555 on 2011-06-08
With the external plugged , open gparted and at the top right side it will list the hard drive , you might have to click to arrow down to the hard drive you want ......  if you don't understand ask more questions , you can really mess up your computer if you do things wrong ...

---

### Post by oldfred on 2011-06-08
If the external was plugged in when you ran the commands, nothing is showing it. 

Does BIOS see the drive? Your computer hardware has to recognize drive first for any software to find it.

---

### Post by Anson S on 2011-06-09
> **oldfred said:**
> If the external was plugged in when you ran the commands, nothing is showing it. 

Does BIOS see the drive? Your computer hardware has to recognize drive first for any software to find it.

The external WAS plugged into the computer when I ran the commands. The odd thing is that I can access the folders and files on the external drive from Ubuntu, however Gparted can't see it.

How do I see if BIOS see's it? I do know that when I'm booted into Windows XP I can see the drive, and I can also see the drive from Ubuntu, but not from Gparted on Ubuntu.

---

### Post by oldfred on 2011-06-09
If you can see it from Ubuntu I do not know why fdisk or parted cannot see the drive. BIOS must then see it or nothing would work.  Many times you can do somethings in a partition, but if a partition table has corruption then changes cannot be made until repairs are made.

Lets run full boot script as it shows many things. 

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

