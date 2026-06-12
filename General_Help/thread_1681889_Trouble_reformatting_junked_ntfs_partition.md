---
title: "Trouble reformatting junked ntfs partition"
date: 2011-02-04
forum: General Help
---

### Post by SnickerSnack on 2011-02-04
I'm trying to reformat a windows partition that doesn't work anymore.  Here is a list of my partitions:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb6cc0bd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         833     6297448+  27  Unknown
/dev/sda2             834       13159    93184000   83  Linux
/dev/sda3           13160       41346   213086129    5  Extended
/dev/sda5           13160       15239    15719571   83  Linux
/dev/sda6           15239       17318    15719571   83  Linux
/dev/sda7           17318       19397    15719571   83  Linux
/dev/sda8           19398       19953     4200966   82  Linux swap / Solaris
/dev/sda9           19953       24287    32764536   83  Linux
/dev/sda10          24287       41346   128961756    b  W95 FAT32
```

sda2 is the partition I'm working with; it was ntfs, but it's now labelled as ext3 after failed attempts to reformat it.  sda1 is the windows recovery partition, and I intend to leave that as is indefinitely.

sda5 has an old ubuntu 9.10 32-bit install, sda6 has my current xubuntu 10.10 64-bit install, sda7 has a new debian install, and sda8 is the ubuntu home directory (shared by both ubuntu installs).  I want to chop up sda10 so I can use some of it for a home directory for the debian install.  To do this, I want to first reformat sda2 so I can use that as extra storage, copy sda10 there, then repartition the space currently used by sda10.

Anyway, I tried using gparted to reformat sda2, but I get this error:

```
GParted 0.6.2

Libparted 2.3

Format /dev/sda2 as ext3  00:00:02    ( ERROR )
    	
calibrate /dev/sda2  00:00:00    ( SUCCESS )
    	
path: /dev/sda2
start: 12595200
end: 198963199
size: 186368000 (88.87 GiB)
set partition type on /dev/sda2  00:00:02    ( ERROR )
libparted messages    ( INFO )
    	
Error informing the kernel about modifications to partition /dev/sda3 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sda3 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
Failed to add partition 3 (Device or resource busy)
```

But the partition isn't mounted, and it isn't being used in any way as far as I can tell.

Help?

---

### Post by Krytarik on 2011-02-05
How about these procedure?:

- reboot, if not done since those error mesage
- delete partition
- apply
- create partition, using the desired file format (ext3/ext4)
- apply again

---

### Post by srs5694 on 2011-02-05
Despite the use of the word "error," what's happened is probably not an error; GParted was just unable to get the kernel to recognize a new partition table -- and GParted didn't even need to change the partition table to just create a new filesystem. (That's not to say that GParted *didn't* change your partition table; it might have done so. It didn't *need* to do so, though.)

You can probably manually mount /dev/sda2 using the "mount" command; or rebooting will probably get everything working as you want. If not, I recommend you try again *after* rebooting using the mkfs utility:

```

sudo fdisk -lu /dev/sda
sudo mkfs -t ext4 /dev/sda2

```

Before you apply the following command, verify that /dev/sda2 is the correct partition based on the fdisk output.

---

### Post by SnickerSnack on 2011-02-16
Thanks for the replies.

Rebooting didn't help, neither did mount (wrong fs, fs not recognized even when I specify it).  I'll try mkfs before deleting the partition.



EDIT: mkfs worked.  I'll probably break up the partition before I use it, so I'll end up deleting it anyway, but at least now I know it's working fine.

Thanks again.


EDIT: Follow-up question: I'm going to use part of this partition as a home directory for a debian install.  Currently, the root directory is located in /dev/sda7, right after my two ubuntu installs.  The two ubuntu installs share a home directory in /dev/sda9, and I decided it would be best to keep separate home directories for different distros (even if they are similar).

Now, is there any reason not to have a home directory outside the extended partition that the root directory is in?  Since /dev/sda2 is earlier in the drive, would it be better to cut ~15 GB of the new primary partition off and reinstall debian there, rather than leaving debian near the end of the disk in a logical partition?  I haven't used the current debian install at all, so reinstalling isn't a problem.

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    12594959     6297448+  27  Unknown
/dev/sda2        12595200   198963199    93184000   83  Linux
/dev/sda3       198965087   625137344   213086129    5  Extended
/dev/sda5       198965088   230404229    15719571   83  Linux
/dev/sda6       230404293   261843434    15719571   83  Linux
/dev/sda7       261843498   293282639    15719571   83  Linux
/dev/sda8       293282703   301684634     4200966   82  Linux swap / Solaris
/dev/sda9       301684698   367213769    32764536   83  Linux
/dev/sda10      367213833   625137344   128961756    b  W95 FAT32

```

---

### Post by Krytarik on 2011-02-16
Phyically you should get the best performance if have those "files" at the start of a disk, which are getting accessed the most. Meaning, preferably Swap space at first, then the OSes you are running the most often.

---

### Post by SnickerSnack on 2011-02-16
Okay.  Thanks.

---

