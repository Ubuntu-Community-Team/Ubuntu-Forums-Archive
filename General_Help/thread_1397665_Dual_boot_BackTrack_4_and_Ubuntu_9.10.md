---
title: "Dual boot BackTrack 4 and Ubuntu 9.10"
date: 2010-02-03
forum: General Help
---

### Post by altjx on 2010-02-03
Anyone know of a noob guide out there on how to dual boot? I believe I've tried to install Backtrack 4 while I had ubuntu but it didnt give me the option to install side by side. I'm pretty new to linux but learning at a good pace, and loving everything so far. Any help would be appreciated, ty =)

---

### Post by jamoncillo on 2010-02-03
nnnnnnnnnope

well... actually... I was folowing this guide:

[http://hydtechblog.com/2009/04/21/how-to-install-backtrack-3-or-4-to-hard-drive-along-with-windows-xp-ubuntu-fedora-opensuse-on-lenovo-thinkpad-x60/](http://hydtechblog.com/2009/04/21/how-to-install-backtrack-3-or-4-to-hard-drive-along-with-windows-xp-ubuntu-fedora-opensuse-on-lenovo-thinkpad-x60/)

but got stuck after the first reboot. however, I think I'm just seeing the light, so I'll go on and let you know if I get lucky

BTW, it's not quite an easy guide, but it does seems to take you through all the steps. Let me know if you need anything

---

### Post by 786souljah on 2010-02-03
I'm triple booting XP, Backtrack 4 and Ubuntu. Here's a short synopsis.

Since you're dual booting I'll leave out XP.

Install backtrack first. 

Make sure to leave to empty partitions, one for swap, the other for the install for ubuntu. I'm sure you can find a short tut on partitioning if you do not know how. A quick search for 'gparted' will get you on your way.

Next install Ubuntu. Make sure to select the proper partition when asked how/where to install ubuntu. Select 'manual' instead of the option to install to the whole disk. In advanced settings, make sure you select the correct partition (the one you'd like to install to) as the root (denoted by '/').

Once done, make sure grub has loaded everything correctly. You may see Ubuntu 8.10 instead of 'Backtrack 4' due to the fact that backtrack is built off of ubuntu.

Another tutorial on grub may help you with renaming.

Hope that helps a bit. Any other questions feel free to keep posting.

---

### Post by jamoncillo on 2010-02-03
yupe. Or, if ubuntu is installed first (which I think is your case) BT4 does allows for manualy setting the partition table.

First make a partition for BT4 in ubuntu, and make it EXT3.
Then, when installing BT$ just choose to assign them manually, and choose your partition as mount point --->  \
then it'll install itself 

HOwever you may need to reinstall the grub after installing backtrack. or at least to update it. Can't tell you for sure 'cause I'm installing BT as the link I gave you says. Altought I'm copying system files from Ubuntu, instead of backtrack, cause apparently my DVD is damaged. That prevented me from installing it from the live session too....

---

### Post by altjx on 2010-02-03
> **jamoncillo said:**
> yupe. Or, if ubuntu is installed first (which I think is your case) BT4 does allows for manualy setting the partition table.

First make a partition for BT4 in ubuntu, and make it EXT3.
Then, when installing BT$ just choose to assign them manually, and choose your partition as mount point --->  \
then it'll install itself 

HOwever you may need to reinstall the grub after installing backtrack. or at least to update it. Can't tell you for sure 'cause I'm installing BT as the link I gave you says. Altought I'm copying system files from Ubuntu, instead of backtrack, cause apparently my DVD is damaged. That prevented me from installing it from the live session too....


Eh, I'm pretty new, that sounds a little complicating. Think I'll just leave it alone, thanks =(

---

### Post by jamoncillo on 2010-02-03
haha

I just finished installing BT4 from the live CD

it's just as installing Ubuntu

click the install file on desktop. choose location, keyboard and once you get to the partition setuo, choose manual (the last option)

If you already setup yur partitions in ubuntu, simply choose the partition you'd like to use as a mount point (by choosing edit partition, and then from the dialog:
use as EXT3, format partition, and in mount point choose just the inverted slash  \

and that's it. wait until it is installed, and reboot

then you'll have to reconfigure grub.
from    [http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)  :  

> 
2).Using Ubuntu 9.10 livecd
Here assuming the Ubuntu partition is sda7,and /boot partition is sda6 (if you have a separate /boot partition).
Boot up ubuntu from the livecd,open terminal and run:

sudo -i
mount /dev/sda7 /mnt
mount /dev/sda6 /mnt/boot  #skip this one if not have a separate /boot partition
grub-install --root-directory=/mnt/ /dev/sda

If you miss &#8220;grub.cfg&#8221; file,use following to recreate:

mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
chroot /mnt update-grub
umount /mnt/sys
umount /mnt/dev
umount /mnt/proc
exit 




and that's it, dude! easy as cake!
I just did it :)

need any help, you can contact me using skype. Jamoncillo, from mexico   (=

hope it helps

---

### Post by altjx on 2010-02-04
Thanks, I just installed BT4 first, then installed Ubuntu 9.10 side by side. Didn't have to do any configuring and it all worked.

---

### Post by jamoncillo on 2010-02-06
> **altjx said:**
> Thanks, I just installed BT4 first, then installed Ubuntu 9.10 side by side. Didn't have to do any configuring and it all worked.

Glad to know it went smooth  =)

Mind marking the thread as solved? ;)

---

### Post by altjx on 2010-02-06
> **jamoncillo said:**
> Glad to know it went smooth  =)

Mind marking the thread as solved? ;)

It should be marked as solved already

---

### Post by jamoncillo on 2010-02-06
nevermind. just realized it's already marked =)

---

### Post by jensbodal on 2010-11-23
> **jamoncillo said:**
> haha

I just finished installing BT4 from the live CD

it's just as installing Ubuntu

click the install file on desktop. choose location, keyboard and once you get to the partition setuo, choose manual (the last option)

If you already setup yur partitions in ubuntu, simply choose the partition you'd like to use as a mount point (by choosing edit partition, and then from the dialog:
use as EXT3, format partition, and in mount point choose just the inverted slash  \

and that's it. wait until it is installed, and reboot

then you'll have to reconfigure grub.
from    [http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)  :  

```
2).Using Ubuntu 9.10 livecd
Here assuming the Ubuntu partition is sda7,and /boot partition is sda6 (if you have a separate /boot partition).
Boot up ubuntu from the livecd,open terminal and run:

sudo -i
mount /dev/sda7 /mnt
mount /dev/sda6 /mnt/boot #skip this one if not have a separate /boot partition
grub-install --root-directory=/mnt/ /dev/sda

If you miss “grub.cfg” file,use following to recreate:

mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
chroot /mnt update-grub
umount /mnt/sys
umount /mnt/dev
umount /mnt/proc
exit 
```



and that's it, dude! easy as cake!
I just did it :)

need any help, you can contact me using skype. Jamoncillo, from mexico   (=

hope it helps

Great advice.  I would add that to figure out the mount point of your Ubuntu partition you can type ```
sudo fdisk -l
```  From there it's just a bit of logical thinking and hopefully you can figure out which Linux partition is Ubuntu and which is BackTrack by the size of the partition.

Here is my output:
>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       33319   267528878+   7  HPFS/NTFS
/dev/sda3           33320       38914    44935982    5  Extended
/dev/sda5           35222       38756    28385280   83  Linux
/dev/sda6           38756       38914     1267712   82  Linux swap / Solaris
/dev/sda7           33320       35221    15277783+  83  Linux


My Ubuntu partition is sda5 and my BT4 partition is sda7, they both use sda6 for swap.

So all I had to do was 
```

sudo -i
mount /dev/sda7 /mnt
grub-install --root-directory=/mnt/ /dev/sda

```

Then reboot, boot into Ubuntu (BT4 partition will be missing from Grub menu), and once there open up a terminal and type ```
sudo update-grub
```.  You should now have all of your OSes bootable from the Grub menu.

---

