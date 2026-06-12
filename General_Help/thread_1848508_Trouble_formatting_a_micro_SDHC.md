---
title: "Trouble formatting a micro SDHC"
date: 2011-09-22
forum: General Help
---

### Post by littlejoe5 on 2011-09-22
Struggling to figure out where to post this. If I got it wrong, please clue me.

This micro SDHC chip came to me unformatted. It is 16GiB Class 2 from Samsung.  I though, "no probolem, I'll just format it myself. " Understood that it was supposed to be Fat32. But I haven't been able to format it. Here's some of the recent history of trying to do that. I have another chip just like it but it is properly formatted, and I was able to Read from and write to it to prepare it for use in an Android pad, in which it is working fine.  But THIS one!.....

I just now tried again - this time to format using Gparted to ext2. The
program finished with an error, and gave me an opportunity to save the
details. These are the details:

GParted 0.6.2

Libparted 2.3
Format /dev/sde1 as ext2 00:05:36 ( ERROR )

calibrate /dev/sde1 00:00:01 ( SUCCESS )

path: /dev/sde1
start: 2048
end: 30916607
size: 30914560 (14.74 GiB)
set partition type on /dev/sde1 00:00:04 ( SUCCESS )

new partition type: ext2
create new ext2 file system 00:05:00 ( ERROR )

mkfs.ext2 -L "" /dev/sde1

Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
966656 inodes, 3864320 blocks
193216 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=3959422976
118 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208

Writing inode tables: done
mke2fs 1.41.12 (17-May-2010)
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read
while creating root dir

========================================

And then the sdhc is not recognised by any program that I have installed.
Not by gparted, testdisk, disk utility, fdisk, or cfdisk. Maybe it will be
when I reboot.

-=-=-=-=-=-=-=-=-=-=-=
I just rebooted, and checked: fdsik -l gives me this:
Disk /dev/sde: 15.8 GB, 15829303296 bytes
255 heads, 63 sectors/track, 1924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b240c

Device Boot Start End Blocks Id System
/dev/sde1 1 1925 15457280 83 Linux
=-=-=-=-=-=-=-=-=-
gparted sees the item as /dev/sde, with one partition "/dev/sde1" which it
says is "filesystem unknown" size 14.74GiB
=-=-=-=-=-=-=-=-=-
Disk Utility identifies it as /dev/sde1 "unknown 16GiB" with a "partition
type: Linux 0x83"
=-=-=-=-=-=-=-=-=-=
if I call cfdisk with this command: "cfdisk /dev/sde" I get this:
"FATAL ERROR: Bad primary partition 0: Partition ends in the final partial
cylind
Press any key to exit cfdisk
=-=-=====
if I use "cfdisk /dev/sde1", I get the interactive screen, and cfdisk
gives this information:
Disk Drive: /dev/sde1
Size: 15828254720 bytes, 15.8 GB
Heads: 64 Sectors per Track: 32 Cylinders: 15095

Name Flags Part Type FS Type [Label] Size (MB)
-------------------------------------------------------------------------------------------------------
sde1p1 Boot Primary Linux 15828.26
-=-=-=-=-=-=-=-=

Hope that makes it clear to somebody. I'm not understanding much of it.

If I'm not mistaken this card is supposed to have a format of fat32, but
it won't format to that either.

Any advice about where to go from here with this?
__________________
"God hath chosen the foolish things..."
Presario SR2027X with Nvidia Gforce 6150 LE Graphix
2G memory - lots of disk space.

---

### Post by cariboo on 2011-09-22
Moved to General Help, as this isn't a Cafe question.

---

### Post by patryk77 on 2011-09-22
```
sudo fdisk /dev/sde
# In the menu, press **d**
# It should say selected partition 1
# Press **p**
# It should list no partitions
# Press **n**
# Press **p** (primary partition 1-4)
# Press **1**
# Press Enter twice to accept default start/stop cylinders
# Press **p**
# It should list a partition with id 83, System Linux
# Press **t** to change the type
# Press **b** Which should say: Changed system type of partition 1 to b (W95 FAT32)
# Press **p**
# It should list a partition with id b and System W95 FAT 32
# If it does, press **w** to write the table

```

If you get a message saying partition is in use and the kernel is using the old table until reboot, reboot.

sudo mkdosfs /dev/sde1

Should be all.

---

### Post by littlejoe5 on 2011-10-06
Thanks for being very specific. I followed your directions exactly (except that the system now calls that SDHC "/dev/sdf") But didn't get the results that you indicated.

From the point in your instructions for fdisk, using the "t" command to change type, here is what I got:

=-=-=-=-=-==-=-======-=-=-=-=-=-=
Command (m for help): t
Selected partition 1
Hex code (type L to list codes): b
Changed system type of partition 1 to b (W95 FAT32)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 5: Input/output error.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)

WARNING: If you have created or modified any DOS 6.x
partitions, please see the fdisk manual page for additional
information.

Error closing file
mint10-2011 mint10 # 
=-=-=-==-=-=-=-==-===-=-=-=-=-=-=

After reboot fdisk with command "p" gives this:
Command (m for help): p

Disk /dev/sdf: 15.8 GB, 15829303296 bytes
255 heads, 63 sectors/track, 1924 cylinders, total 30916608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b240c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1            2048    30916607    15457280   83  Linux

=-==-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-

The system does not recognize it as a useable file system.  Gparted says that the file system is "unknown"

:confused:

---

### Post by patryk77 on 2011-10-06
> WARNING: Re-reading the partition table failed with error 5: Input/output error.
Error closing file

That's weird, I have never seen such an error before...

I take it you did run this as root, or with sudo, as otherwise fdisk shouldn't even run?

```
/dev/sdf1 2048 30916607 15457280 83 Linux
```
The partition didn't actually change types. Could it be that the card is physically set to read-only? They usually have a little pin you can slide.

---

### Post by littlejoe5 on 2011-10-07
My eyes aren't as good as they once were. I can see the "read-only" lock on the sd cartridge that adapts the sdhc micro to the sd slot on the computer.  it is definitely in the unlocked position, which I assume is R/W.  But I can't see that there is a lock on the tiny little micro SDHC.

And yes, I was running as root. As you noted, fdisk won't even run otherwise.

Hate to throw the thing away. It cost me about $20.00. I at least might get some education out of it.:-k

---

### Post by dcstar on 2011-10-07
> **littlejoe5 said:**
> 
...........
Hate to throw the thing away. It cost me about $20.00. I at least might get some education out of it.:-k

Use **gparted** to write a new partition table to it and try again.

---

### Post by HermanAB on 2011-10-07
Wait, you already know fdisk now.  Just continue with that one. (Gparted is a GUI front end to fdisk that makes it more difficult...)

Here is how I do these things in plain English:
Plug device in
Run dmesg to see the device name
Run fdisk with the device name
Delete all the current partitions
Make a new partition
Set the type of the new partition to Win95
Now use mkfs.vfat to format the new partition
Be sure to also set the volume label, because that is used by the automounter
La voila!

For details, read the man pages - they are good for fdisk and mkfs.vfat.

---

### Post by dcstar on 2011-10-07
> **HermanAB said:**
> Wait, you already know fdisk now.  Just continue with that one. (Gparted is a GUI front end to fdisk that makes it more difficult...)
.........

gparted is a GUI front end to parted, **not** fdisk.

---

### Post by patryk77 on 2011-10-07
> **littlejoe5 said:**
> I can see the "read-only" lock on the sd cartridge that adapts the sdhc micro to the sd slot on the computer.  it is definitely in the unlocked position, which I assume is R/W.  But I can't see that there is a lock on the tiny little micro SDHC.

Yeah, that is correct. usually the adapters have the pin for micro cards.

---

