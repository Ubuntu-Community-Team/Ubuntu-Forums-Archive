---
title: "Making more room for Ubuntu"
date: 2010-10-25
forum: General Help
---

### Post by marj4 on 2010-10-25
Hello,hopefully I am posting in the correct area. I setup a dual boot setup on my son's computer,Windows Vista and Ubuntu.

I install Ubuntu using the Ubuntu Windows installer option. Now he is getting no disk space error every time it goes to do an update.Looking under the "Disk Utility",it says capacity 18 gb.So I thought it would be a simple matter of resizing the partition using gparted but the hard drive isn't partition.

So how do I give Ubuntu more room? The hard drive is 500gb and the computer was built by my son so there is no brand name.

---

### Post by cpmman on 2010-10-25
Click on the WubiGuide link in my signature.  There is a number of options for increasing disc space and or separating the / and /home.  There is also a guide for making the wubi install into a true dual boot.

---

### Post by lavinog on 2010-10-25
Can you post the output of:
```

sudo fdisk -l

```

Also you might want to find out what is consuming your space.
A couple of things you can do to free up space is run:
```

sudo apt-get autoremove
sudo apt-get clean

```

As for increasing space, depending on how much unpartitioned space you have:
If you have no unpartitioned space, you will have to shrink an existing partition (like windows.)  Newer versions of windows apparently do not like to be shrunk by linux, so you will need to boot into windows and shrink the partition from there.

If you have unpartitioned space (or recently created some by shrinking windows), you have two options: (1) grow your current ubuntu partition, or (2) create a new partition for storage.

I prefer #2 as it adds a separation of critical / non-critical data, and it is much quicker and safer to implement.

#1 involves booting into a live cd and running gparted to grow the current partition.  This sometimes can take a long time.

#2 involves booting into a live cd and running gparted to create a new (ext4) filesystem.  Once complete boot back into windows and mount the new partition.
I usually keep my pictures and videos on a separate partition.

---

### Post by marj4 on 2010-10-25
Here is the resuls of fdisk:


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2637f0a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488384512    7  HPFS/NTFS

---

### Post by Mark Phelps on 2010-10-25
The results of fdisk confirmed what we already suspected -- you have installed Ubuntu using Wubi, in which Ubuntu creates a large file in the NTFS partition that serves the purpose of a Linux filesystem.

Therefore, it shares space with the NTFS partition.

You have to follow the Wubi links already provided to learn how to grow the space that Wubi initially allocated.  You can't do that with standard partitioning tools (i.e., GParted) because Ubuntu is  not installed in a separate partition.

---

### Post by marj4 on 2010-10-26
Thank you for the help! Much appreciated!

---

### Post by cpmman on 2010-10-27
If you are satisfied that your difficulty is resolved please use the Thread Tools at the top to mark the thread Solved.

---

