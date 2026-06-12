---
title: "reading a nfts drive"
date: 2006-03-29
forum: General Help
---

### Post by kurakusan on 2006-03-29
reading from windows drive.

I have this slave drive which ubuntu recognizes, but it can't see any partitions on.

sudo fdisk -l  prints:

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
16 heads, 63 sectors/track, 158816 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

and then shows no partitions so i can't find a way to mount it.:confused:

---

### Post by ispmarin on 2006-03-29
The windows drive has fat32 or ntfs partitions? Did you tried to mount it with
mount /dev/hdb<n> /mnt? (where n is the partition number)?

---

### Post by Ramses de Norre on 2006-03-29
[https://wiki.ubuntu.com/MountingWindowsPartitions?highlight=%28windows%29]("https://wiki.ubuntu.com/MountingWindowsPartitions?highlight=%28windows%29")

---

### Post by kurakusan on 2006-03-29
unfortunately that doesn't seem to work. since it cannot recognize any partition.  both of those require that the partition is known

it tells me that hdb was not found under /etc/fstab or /etc/mtab.

Earlier another version of linux, beatrix, seemed to have recognized it. Its no longer doing it now. I even tried removing it and placing it in a windows pc which refused to recognize it even though it Plug and play

---

### Post by aysiu on 2006-03-29
Can you plug it in and then post the output of these three separate commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by kurakusan on 2006-03-29
bea@ttyp0[bea]$ sudo fdisk -l

Disk /dev/hda: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2446    19647463+  83  Linux
/dev/hda2            2447        2491      361462+   5  Extended
/dev/hda5            2447        2491      361431   82  Linux swap

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
16 heads, 63 sectors/track, 158816 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
bea@ttyp0[bea]$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/root             3.2M  1.5M  1.7M  47% /
/dev/scd0             183M  183M     0 100% /cdrom
/dev/cloop            554M  554M     0 100% /BEATRIX
/ramdisk               90M  3.6M   86M   5% /ramdisk
/dev/hda1              19G  2.5G   16G  15% /mnt/hda1
/dev/scd0             183M  183M     0 100% /mnt/cdrom
df: `nfts': No such file or directory
bea@ttyp0[bea]$ cat /etc/fstab
/proc      /proc       proc   defaults            0 0
/sys       /sys        sysfs  noauto              0 0
/dev/pts   /dev/pts    devpts mode=0622           0 0
/dev/fd0   /mnt/floppy auto   user,noauto,exec,umask=000    0 0
/dev/cdrom /mnt/cdrom  auto   user,noauto,exec,ro 0 0
/dev/cdrom1 /mnt/cdrom1  auto   users,noauto,exec,ro 0 0
# Added by KNOPPIX
/dev/hda1 /mnt/hda1 ext3 noauto,users,exec 0 0
# Added by KNOPPIX
/dev/hda5 none swap defaults 0 0
# Added by KNOPPIX
/dev/hdb /mnt/hdb auto noauto,users,exec 0 0
](*,)

---

### Post by aysiu on 2006-03-29
Okay, I see now what you meant in your original post.

So there is a /dev/hdb... just no /dev/hdb1 or /dev/hdb2, etc.

What's with the Knoppix-added entries to your /etc/fstab? That seems odd to have in Ubuntu. Are you actually using Knoppix?

Maybe you can try just guessing that it's /dev/hdb1?
You could also try loading up a program like *gparted* to see how it recognizes the drive...

---

### Post by kurakusan on 2006-03-29
or sorry about that i was on a different OS while doing that (the results were the same however). I shoulda thought about that.

Gparted just says its unallocated. :(

is there any hope for salvaging the data off my hard drive?:-({|=

---

### Post by ispmarin on 2006-03-30
If even gparted did not find any partition there, not sure that you will be able to find any salvable data there... there is plenty of software to try to rescue some data (just don't remember any for linux now... sorry)

---

