---
title: "file systems/what is best structure"
date: 2012-02-03
forum: General Help
---

### Post by gbrowning on 2012-02-03
I am running 11.10 on a Core i7 system with a 30GB SSD as boot/system, 2 750GB internal drives and a external 750 using ESATA to a Toaster.
    I just installed a Bluray writer and am dying to test it out but am having trouble generating or downloading a 50GB iso file. At this point all but the system drive are nearly empty.
    The problems seem varied but must have a common problem at the root. Most recently when downloading an ISO torrent using transmission the error "file system is read only" appeared when the download reached about 4.9 GB.  When downloading the same ISO file a day before the message "Low disk Space" appeared when the file reached about the same size.  I experienced the same error "Low Disk Space" a day earlier, again the same ISO file.
     While Transmission is saving the files to one of the 750GB internal drives  DiskUtility shows the System drive to be full.  I have kept between 4 and 8 GB of the system drive as free space.  Disk Utility and Nautilus and gparted do not agree on the amount of the file space that has been used.
     First question...how did the file system change to read only? If it were "Read Only" to begin how did it begin to write at all?
     Second question...What is the best file system for Ubuntu? I had a variety of systems on the disks but during this cleaning have changed over to EXT4, but now is a good time to come up with a good strategy.
     Third question....should I put the Home folder on a separate disk from the system drive?
     TIA

---

### Post by oldos2er on 2012-02-03
Can you run these two commands (separately) and post their output here? ```
df -h
sudo fdisk -l
```

---

### Post by gbrowning on 2012-02-03
df
 Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              29G   23G  3.8G  86% /
udev                  3.0G  4.0K  3.0G   1% /dev
tmpfs                 1.2G  1.2M  1.2G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  3.0G  296K  3.0G   1% /run/shm
df: `/root/.gvfs': Permission denied
/dev/sdb1             321G   16G  290G   6% /media/DevSDB_1
/dev/sdb2             328G   22G  290G   7% /media/New Volume_
/dev/sdc3             440G   47G  371G  12% /media/Internal ext4

sudo

---

### Post by gbrowning on 2012-02-03
sudo fdisk -l

Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000edbb2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    59865087    29931520   83  Linux
/dev/sda2        59867134    62531583     1332225    5  Extended
/dev/sda5        59867136    62531583     1332224   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  1465149167   732574583+  ee  GPT

Disk /dev/sdd: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00015abd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd2        33144832  1381059854   673957511+  83  Linux
/dev/sdd3      1381059855  1465144064    42042105   82  Linux swap / Solaris

---

### Post by gbrowning on 2012-02-03
At this moment gparted is removing the GUID partition.  A remnant of a dual boot.  I don't think that was the cause but......

---

### Post by oldos2er on 2012-02-03
I don't know anything GUID, but I'm sure you'll get responses from others who do.

Since your home folder is in your root partition, that would explain why you can't save a 50GB file to a 30GB partition. Transmission defaults to saving files to your /home/user folder. Maybe you could set up one of the 750GB drives as /home? Just a thought.

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by gbrowning on 2012-02-04
Thanks for the advice , and for the Lovecraft quote.  Transmission has been instructed to place the files on one of the 750GB drives but it does seem to be using the Home folder for something.  I will migrate the home folder over, then try downloading the file again.  It will take a few hours before the file will be large enough for me to know if this worked.

---

### Post by gbrowning on 2012-02-05
Thank you Ann, thank you oldos2r.
The Home folder was migrated over to a 750GB drive.  This did not go smoothly but it seems to have worked.  The incoming file is well over 5GB, Transmission has reserved a 50GB block and the numbers add up.
   Now to find out how to force Transmission to use only a specified disk area.

---

