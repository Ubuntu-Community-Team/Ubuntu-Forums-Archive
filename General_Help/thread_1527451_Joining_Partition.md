---
title: "Joining Partition"
date: 2010-07-09
forum: General Help
---

### Post by JCM_Pico on 2010-07-09
Hi all
I recently changed my hard drive and I've copied all the content, bite by bite, from the old disk to the new one, using partimage. 
Now when I boot the system I run the command's above and it appears to have one partition with my installation and other partition with no space occupy. Is really this that happened 
If yes, how can I merge the partition
[I][B]
df -lk[/B][/I]
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             92196896  45546496  41967036  53% /
none                   1023084       292   1022792   1% /dev
none                   1030040      1452   1028588   1% /dev/shm
none                   1030040        88   1029952   1% /var/run
none                   1030040         0   1030040   0% /var/lock
none                   1030040         0   1030040   0% /lib/init/rw

***fdisk -l***
isk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cceaf

---

### Post by quimkaos on 2010-07-09
if your are using Ubuntu desktop try install and use gparted.

---

### Post by JCM_Pico on 2010-07-09
I got gparted from the repository... but I don't want to make any mess.
Any body can guide me throw this

---

### Post by audiomick on 2010-07-09
Can you start gparted and post a screen shot of what it shows you? That will aid anyone who can help you.

---

### Post by JCM_Pico on 2010-07-09
[LEFT]Here is the screen shot of  gparted, this is strange for me cause its says that I'm occupying lots of space, when I'm only using about 50 GB....
[/LEFT]

---

### Post by john newbuntu on 2010-07-09
Also that output from "sudo fdisk -l" appears incomplete.  If so, please post the complete output. Or was that all you got?
Also what were your original partitions like?

---

### Post by JCM_Pico on 2010-07-09
> **john newbuntu said:**
> Also that output from "sudo fdisk -l" appears incomplete.  If so, please post the complete output. Or was that all you got?
Also what were your original partitions like?

It was all I got from fdisk -l.
The primordial disk had no partition, it was fully occupied by my ubuntu installation ( 100 Gb disk withe 41Gb avaiable).

---

### Post by john newbuntu on 2010-07-09
No partitions on the old drive! Would be interesting to know how you managed to do that.

Please check if partimage supports ext4 filesystem.  Its homepage says it is not but maybe I am not interpreting it correctly.
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

Does the data in it look ok to you?  You might want to check your filesystem first by doing fsck from a liveCD.  If that comes out ok, login and run "cd /; sudo du -xk --max-depth=1" to check the space occupied by the various directories.  I am not sure on where it got its bytes from.

---

### Post by quimkaos on 2010-07-09
seams fine to me! you have 1MB of unallocated space and i think you shouldn't change anything. I think almost every time i partitioned an hard drive it ends up with some unallocated space at star or ending of the drive, and i think this is some kind of "reserved" space.

just one question: why have you replaced the hard drive? the old one failed?

and has john said in the old disk you should at least have 2 partitions 1 for ext4 and other to linux-swap.

---

### Post by JCM_Pico on 2010-07-09
> **quimkaos said:**
> seams fine to me! you have 1MB of unallocated space and i think you shouldn't change anything. I think almost every time i partitioned an hard drive it ends up with some unallocated space at star or ending of the drive, and i think this is some kind of "reserved" space.

just one question: why have you replaced the hard drive? the old one failed?

and has john said in the old disk you should at least have 2 partitions 1 for ext4 and other to linux-swap.

I'm sorry for the inaccuracy, in the old system I had the /dev/sda1 partition, extended and linux-swap.
I replaced the drived because I need more space for having some data in my computer and make a dual boot with windows as well.
The most strange thing its that in GParted the unused space that I see in /dev/sda1 is the exact size has the free space that I had in the older disk.
I've tried to use remastersys, but the backup was too large to use it...

---

### Post by QLee on 2010-07-09
JCM_Pico,

Did you read much about partimage before you started?

From the site main page:
** "Limitations**

 Partimage does not support **ext4** or **btrfs** filesystems."

---

### Post by quimkaos on 2010-07-09
meaning that about 150 GB are somewhat incorrectly occupied and you should have that 150 GB in unallocated space, since you moved from a 100GB disc to a 320GB! that's odd!

I usually use ghost for this type of jobs and never got that problem....

---

### Post by JCM_Pico on 2010-07-09
> **QLee said:**
> JCM_Pico,

Did you read much about partimage before you started?

From the site main page:
** "Limitations**

 Partimage does not support **ext4** or **btrfs** filesystems."


I tooth I could backup to ext3 file system.
So this way off backing up is a big big mess.
what's the best way of doing this.
I read that rmastersys is very powerfull, but when I try to backup the hole system it turns to be too big.
I also read about dd_rescue, anybody could give me some help

---

### Post by quimkaos on 2010-07-09
i would suggest you (again) to use ghost, since it's the only one i have experience with. I usually do this by using Hiren's boot cd. you can also use ghost for linux: [http://g4l.sourceforge.net/](http://g4l.sourceforge.net/)

---

### Post by oldfred on 2010-07-09
I do not even back up my system, just my data, /home, list of installed apps, and a few files from /etc that I have manually edited. I plan on reinstalling if it ever crashes anyway.

I believe in clean installs so I know the system is set up and working correctly. Since you have the old drive (and I assume it still works). I would just do a new instal to the new drive. Create partitions in advance with / (root) 25GB, swap at 2GB or RAM memory size if you ever want to hibernate and the rest as /home (or add another for data or additional installs if you ever want to experiment). You now have lots of room and can do a little planning in advance on how you want your partitions laid out rather than just replicating the old.

Copy old /home to your new. Make a list of installed apps and reinstall. If you had any custom settings in /etc copy them over and you have replicated but improved your system.

You only have to do part of the standard move home instructions if you do a new install.
To move /home uses rsync  (cp with -a should also work):
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

### Post by quimkaos on 2010-07-09
i agree with oldfreed... i also prefer clean installs... but i don't even back my home directory, only my files and the entire folder of Thunderbird.

---

### Post by JCM_Pico on 2010-07-09
> **oldfred said:**
> I do not even back up my system, just my data, /home, list of installed apps, and a few files from /etc that I have manually edited. I plan on reinstalling if it ever crashes anyway.

I believe in clean installs so I know the system is set up and working correctly. Since you have the old drive (and I assume it still works). I would just do a new instal to the new drive. Create partitions in advance with / (root) 25GB, swap at 2GB or RAM memory size if you ever want to hibernate and the rest as /home (or add another for data or additional installs if you ever want to experiment). You now have lots of room and can do a little planning in advance on how you want your partitions laid out rather than just replicating the old.

Copy old /home to your new. Make a list of installed apps and reinstall. If you had any custom settings in /etc copy them over and you have replicated but improved your system.

You only have to do part of the standard move home instructions if you do a new install.
To move /home uses rsync  (cp with -a should also work):
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

I have considerable amount of programs that I need to download, configure and compile... and that takes  me more than a day to do it all.

>  i would suggest  you (again) to use ghost, since it's the only one i have experience  with. I usually do this by using Hiren's boot cd. you can also use ghost  for linux: [http://g4l.sourceforge.net/](http://g4l.sourceforge.net/) 
I will give a try to ghost...
its just simply make a bootable usb device with the iso and follow some steps, or it got some more tricky specs

---

### Post by quimkaos on 2010-07-09
i think it's a bootable cd and you have to have both HDs connected. Basically you select the source and the target device and it will duplicate your data, leaving the rest of the space as unallocated. i suggest that you wipe the new drive, turn it to unallocated space again. just don't choose the wrong source HD. hehehe

---

### Post by JCM_Pico on 2010-07-09
I gave up on this, I just reinstall the hole system
Thank you all for the time and effort  :D

---

