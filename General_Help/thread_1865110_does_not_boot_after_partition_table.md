---
title: "does not boot after partition table"
date: 2011-10-19
forum: General Help
---

### Post by saias on 2011-10-19
Hello,

I just did something very stupid...

through Gparted I choose the option to create a partition table (dont ask why) and although I received the message that this would erase my data I still proceeded. I kept working since nothing changed and after a few hours I had to reboot and this is when my system wouldnt reboot since it cant find a bootable device.

Im currently logged in through a cd and wandering if there is any solution to that... 

I do probably deserve the re-installation but please let me know if there is anything I can do!

I am using 10.10

thanks

---

### Post by garvinrick4 on 2011-10-19
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")
Run this in your live cd and we will see if you have anything left in Ubuntu partition to boot with.

---

### Post by saias on 2011-10-19
thanks for the answer

this is what i get:

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System



"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)

---

### Post by garvinrick4 on 2011-10-19
You got nothing left but a blank HDD so while in live Cd you are using now.
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download") 
Click on button next to 11.10 and can get 10.04 and download and BURN a new CD or USB and
reinstall. There is a bunch of "show me hows' on that same page as given. 
"gparted" and other partitioning tools are a powerful applications, I imagine you know that now.
10.10 downloads you want desktop of whatever you use 64 or 32 bit.
[http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/)

---

### Post by saias on 2011-10-19
thanks for you answer

---

