---
title: "Expanding LVM partition"
date: 2011-10-17
forum: General Help
---

### Post by hojjat on 2011-10-17
I installed Ubuntu 11.10 using an encrypted LVM following the instructions on this page:

[http://www.linuxbsdos.com/2011/05/10/how-to-install-ubuntu-11-04-on-an-encrypted-lvm-file-system/]("http://www.linuxbsdos.com/2011/05/10/how-to-install-ubuntu-11-04-on-an-encrypted-lvm-file-system/")

At the time, I set my /root to almost 10 GB and my /home to almost 100 GB. Here is the output of df -h on my machine:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/VG-root   9.4G  4.6G  4.4G  52% /
udev                  1.6G  4.0K  1.6G   1% /dev
tmpfs                 656M  932K  655M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  1.6G  136K  1.6G   1% /run/shm
/dev/sda1             447M   28M  395M   7% /boot
/dev/mapper/VG-home    94G  3.9G   86G   5% /home

```

Here is the output of vgdisplay:
```

  VG Name               VG
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  4
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                3
  Open LV               3
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               465.29 GiB
  PE Size               4.00 MiB
  Total PE              119115
  Alloc PE / Size       27831 / 108.71 GiB
  Free  PE / Size       91284 / 356.58 GiB

```

As you can see, my hard-disk is 500GB so I want to expand the LVM partitions to use all my disk. I have three questions:

(1) How can I expand these partitions now? (Link to step-by-step instructions appreciated).

(2) Should I only expand /home? Or should I expand the root (/) as well? When I install new software, which one of them is used mostly? Where do /opt and /usr and /etc belong to? Do they count against my 10 GB / or against my 100 GB /home?

---

### Post by bodhi.zazen on 2011-10-17
The thing that is nice about LVM, you can expand your partitions as needed.

Most of your data is probably going to be in /home.

There is no single right answer to your questions, I suggest you use Ubuntu for a while and add space as needed.

For additional details see: 

[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

---

### Post by smurphy_it on 2011-10-17
I guess the first question would be why would you want to extend the sizes ?  The good part of LVM is the ability to increase/decrease LVs.  If you allocated all of your available space from your VG, you won't have any left to allocated to an LV at a later point if required.

It doesn't look like you need additional space (right now) according to your disk layout.  Personally, I would hold off on doing that until you need the space.

commands for reference:

pvs -- stats on your Physical Volumes
vgs -- stats on your Volume Groups
lvs -- stats on your Logical Volumes
vgdisplay - More details on a Volume Group
lvdisplay - more details on a Logical Volume
vgextend -- command for adding an additional disk into a Volume Group
lvextend -- command for increasing/decreasing the logical volume size

NOTE:  Typically when one increases/decreases space of a Logical Volume it is done in two steps (a) changing the logical volume size (b) changing the size of the file system for that logical volume.
IMPORTANT:  If you are increasing an LV, you would first increase the LV, and then increase the FS (for that LV).  If you are 'decreasing' you have to do it in the reverse order, otherwise you'll fry that entire LV.

Increase -- lvextend then fsresize with increase fs with resize2fs
Decrease -- resize2fs then decrease with lvextend

A link on changing sizes:
[http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html](http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html)

---

### Post by hojjat on 2011-10-17
Both good answers.

The reason I need more space is because I'm going to install VirtualBox and run some virtual machines on it. The images of those machines are going to consume space on my /home, so I need to expand home before hand.

However, I'm not sure what happens when I install programs. Their files are stored in /etc, /usr, /bin and /lib right? If so, does it mean I may run out of space on my 10 GB / partition as I add new software?

And finally, the way i understand it, I should use the Ubuntu Recovery Mode to be able to unmount /home and resize it, correct?

---

### Post by bodhi.zazen on 2011-10-17
> **hojjat said:**
> Both good answers.

The reason I need more space is because I'm going to install VirtualBox and run some virtual machines on it. The images of those machines are going to consume space on my /home, so I need to expand home before hand.

However, I'm not sure what happens when I install programs. Their files are stored in /etc, /usr, /bin and /lib right? If so, does it mean I may run out of space on my 10 GB / partition as I add new software?

And finally, the way i understand it, I should use the Ubuntu Recovery Mode to be able to unmount /home and resize it, correct?

you should manage your partitions from a live CD, see the link I gave you.

---

### Post by smurphy_it on 2011-10-18
You have 86GB available in home at the moment.  If that is not enough, by all means increase it.  I would suggest NOT using all space currently allocated to your VG.  That way, at some point if you all of sudden have a need to increase any of the other file systems, you'll have the ability to do just that.

VirtualBox will install all of it's files within it's Virtual Disk.  This Disk is created when you initially build that o/s.  All of these virtual disks are stored within your home folder.

---

