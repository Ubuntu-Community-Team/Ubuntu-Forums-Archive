---
title: "NTFS signature is missing"
date: 2010-07-18
forum: General Help
---

### Post by akashi on 2010-07-18
Hi, I have a serious problem that I must have fixed. I have a dual boot of Ubuntu 10.04 and Windows 7.

I have 2 hard drives on the system, a 500GB and a 1TB drive.
```
root@akashi-desktop:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3e67485a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        5235    41943040    7  HPFS/NTFS
/dev/sda3            5235       57452   419430400    7  HPFS/NTFS
/dev/sda4           57452       60802    26907649    5  Extended
/dev/sda5           57452       57701     1998848   82  Linux swap / Solaris
/dev/sda6           57701       60802    24907776   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44edd366

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       65271   524286213+   7  HPFS/NTFS
/dev/sdb2           65271      121601   452470784    7  HPFS/NTFS

```
All the drives were working fine until I tried to copy a file from my Ubuntu drive (/dev/sda6) to a NTFS drive (/dev/sdb2) via drag and drop. It didn't work so I became stupid and tried various commands:
```
sudo cp file /dev/sdb2
sudo cp file /dev/sdb2/file
sudo chmod 755 /dev/sdb2
sudo chmod 777 /dev/sdb2
sudo chmod -u /dev/sdb2
sudo cp file /media/sdb2/file
```
Since the drive (sdb2) was already mounted I was able to see "file" show up on the NTFS drive (sdb2) with the last command above.

After I rebooted onto Windows 7, I found my F:\ drive (sdb2) showing up as a RAW filesystem. Windows 7 asks to reformat and I press NO as I have a lot of files on that drive.

I rebooted onto Ubuntu again, during boot it says cannot mount to /dev/sdb2 and to press "S" to skip. I pressed "S" and saw sdb2 not mounted. I tried this command:
```
root@akashi-desktop:~# mount -t ntfs /dev/sdb2 /media/sdb2
NTFS signature is missing.
Failed to mount '/dev/sdb2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```
Someone please help me fix this drive without formatting it! fdisk shows the filesytem as NTFS so it must still be fixable I hope.

---

### Post by The Cog on 2010-07-18
> sudo cp file /dev/sdb2
That's not good. This command will have overwritten the start of the partition with your file contents - probably overwriting the NTFS filesystem description headers and stuff. At this stage, you need to reformat the partition and restore from your backup. If you don't have a backup, you probably need a data recovery utility of some sort, but I'm not strong on that subject. The names photorec and testdisk come to mind but I've never used them.

---

### Post by akashi on 2010-07-18
Hello, thank you very much for your reply.

I was able to use "Active Partition Recovery" on Windows and restore the RAW drive back into NTFS. The "Primary Boot Sector was corrupted and I was able to copy the correct values from the "Copy of Boot Sector"

The file I copied to the /dev/sdb2 was a 350MB file and therefore it has overwritten some of my files on the drive. I lost a lot of files, but have saved many too.

This is a lesson I will never forget!

Can someone advice me what is the best way of clearing the Partition Table from both my drives and create new ones? I would like to build the partitions from scratch. As you can see from my 1st post "Partition 1 does not end on cylinder boundary" Time for a fresh start.

Thanks in advance.

---

### Post by The Cog on 2010-07-19
I'm glad you managed to recover so much.

I wouldn't worry too much about the partition not ending on a cylinder boundary. I don't think that alone is reason to repartition.

If you do want to repartition, just using a partitioning tool such as gparted to delete all the existing partitions should be enough. If you really want to go all the way, this command will overwrite the partition table and the bootloader with zeros:
> sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
For the benifit of anyone else reading this: **make sure** you get the **right device**!

---

### Post by akashi on 2010-07-19
Hi all, just an update to say that I have **NOT** lost any files!

After rebooting my Windows 7, all my files showed up on the drive.

If anyone has an NTFS drive showing up as RAW, use Active Partition Recovery. Just right click on your partition and select "Fix Boot Sector"

Hope this helps someone in the future.

---

### Post by mebunto on 2012-02-26
You might use minitool - I just did successfully, and it's free!

[http://www.minitool-partitionrecovery.com/download.html](http://www.minitool-partitionrecovery.com/download.html)

---

