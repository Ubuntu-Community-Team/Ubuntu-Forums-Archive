---
title: "Repair MBR and Partition Table."
date: 2011-05-11
forum: General Help
---

### Post by Prince Valiant on 2011-05-11
Hello.

This post is a follow up to this one: [http://ubuntuforums.org/showthread.php?t=1752578]("http://ubuntuforums.org/showthread.php?t=1752578").

My computer is an IBM R52 running Windows Professional (previously dual-booting with Ubuntu 10.10, but that's gone now, and I don't dare reinstall it until the HDD partitions and mbr are properly working again).  

I think that the shred command mentioned there simply messed up my MBR, and maybe my partition table.  Here's the partitions on my HDD:

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7e93bd30

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4719    37905336    7  HPFS/NTFS
/dev/sda2            6676        7296     4974480   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            4720        6675    15711530+   5  Extended

Partition table entries are not in disk order

Disk /dev/sdb: 4022 MB, 4022337024 bytes
124 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005a8b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1021     3924693   83  Linux

```

sdb1 is a flash drive I installed Ubuntu on.  

sda1 is Windows XP.
sda2 is the IBM Recovery Partition.
sda3 is the Extended partition that used to contain Ubuntu.

My question is, is it safe to use something like SuperGrub to repair the MBR?  I really don't want to mess up the Windows and recovery partitions.  I've done plenty of research on this, but am not confident until someone says that it works in my case.  
:-D

Thanks in advance.

-Val

---

### Post by grahammechanical on 2011-05-11
I have seen other posts where the recommendation was to use a Windows tool to make the MBR repair. If you google windows mbr repair you will get some links that might help.

Regards.

---

### Post by dragonfly41 on 2011-05-11
try this ..

[http://www.ntfs.com/mbr-damaged.htm](http://www.ntfs.com/mbr-damaged.htm)

---

### Post by antaios256 on 2011-05-11
the easiest way to repair the mbr after removing a linux installation is to boot into revoery console (using a windows 7 dvd) once in the console the comand is
```

bootrec /fixmbr

```

note this will repair the windows mbr and remove grub/lilo entirely

---

### Post by seawolf167 on 2011-05-11
As mentioned above, I suggest using the Windows 7 Recovery disk and repairing the MBR

i.e. fixmbr, fixboot like mentioned in the previous post

This will wipe GRUB2 and allow Windows to boot.

After that, follow the [guide here ]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu")to reinstall GRUB2 and search for other OS's with the os-prober.

You can find Windows 7 Recovery [disks here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/").

---

### Post by Quackers on 2011-05-11
The partitions look fine to me. What are you trying to fix exactly?

---

### Post by Prince Valiant on 2011-05-12
Hey!

Thanks for all the help.  I used Dragonfly's link to learn a bit more about the MBR; then I used the other suggestions and used a Windows XP disk to reinstall the Windows MBR.  

That's all I've had time for, yet.  I think I'll have a chance in the next few days to reinstall Ubuntu.

I'm not sure if the IBM Recovery partition is still there.  I'm not sure if it's worth keeping.

I'll call this thread solved!

-Val

---

### Post by antaios256 on 2011-05-13
glad to see you got it working, just let us know if you need more help

---

### Post by Prince Valiant on 2011-05-17
Final update:

Turns out reinstalling the windows MBR didn't make gparted see anything on the HDD-it still thought the whole thing was unallocated.  

I booted into windows, and ran this program in the 'run' window:
```
diskmgmt.msc
```
Then I used that to delete the original Ubuntu partition (which had survived the windows MBR installation).

Then I booted into my Ubuntu 11.04 installation disk, and went straight to the install menu; it recognized my partitions. :-D

The former Ubuntu partition was designated as unallocated, so I made that into swap space and a partition for Ubuntu.  

It all works!  Thing is,```
sudo fdisk -l
``` tells me the partitons aren't listed in the same order they are on the drive.  I can't account for that.

I guess that when I originally tried to shred the Ubuntu Partiton, I simply shredded the partion's entry in the MBR. I remember at one time seeing the actual partition entries, and noticing that the 15GB Ubuntu Partition had a partition type which was all zeros.

-Val

---

