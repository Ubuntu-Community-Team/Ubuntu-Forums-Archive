---
title: "Problems with USB stick"
date: 2011-04-04
forum: General Help
---

### Post by DeMus on 2011-04-04
Hi,
I have a 1GB USB stick which holds files. I can read those files, no problems here.
When I have Nautilus open I see the files, I can select them and throw them away. BUT, when I press F5 (redraw the screen) all files are back.
I can not write new files on it, i can not delete the partition, I can not reformat the stick because it is read-only. I have tried gparted, I have tried gnome-disk-utility and nothing works. I have tried to reformat in Windows but there I get the same message.
The stick is formatted in FAT so Windows can also read it. There is NO read/write switch on the stick which could be in the wrong position. Still I can't use the stick anymore.
Who has an idea of what to do to make this stick writable again?

---

### Post by DeMus on 2011-04-04
Bump.
Who can help me guys? Please.

---

### Post by blueridgedog on 2011-04-04
I would try manually deleting the partition, writing the table, then recreating the partition with fdisk from the terminal.

If you post the output of 

```
sudo fdisk -l
```

I can get you some syntax on the operation.

---

### Post by wolfgangmcq on 2011-04-04
> **blueridgedog said:**
> I would try manually deleting the partition, writing the table, then recreating the partition with fdisk from the terminal.

**Gaack**! That seems like it would erase all the data, too! Before you do that, check if the disk is full. I once had a flash drive with the same symptoms, and the problem turned out to be that it was full. (On the desktop, right-click on the disk & choose Properties)

---

### Post by DeMus on 2011-04-05
> **blueridgedog said:**
> I would try manually deleting the partition, writing the table, then recreating the partition with fdisk from the terminal.

If you post the output of 

```
sudo fdisk -l
```

I can get you some syntax on the operation.

Here is the outcome of the instruction you mentioned:

```
sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8b328b32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6091    48924672   83  Linux
/dev/sda2            6091       60802   439460864   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008807c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488385536   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b1dd1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   83  Linux

Disk /dev/sdd: 1031 MB, 1031798784 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d38d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         126     1007584+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(124, 254, 63) logical=(125, 112, 51)
```

The disk I am talking about is sdd at the bottom of the list.

---

### Post by DeMus on 2011-04-05
> **wolfgangmcq said:**
> **Gaack**! That seems like it would erase all the data, too! Before you do that, check if the disk is full. I once had a flash drive with the same symptoms, and the problem turned out to be that it was full. (On the desktop, right-click on the disk & choose Properties)

It's okay if all data is erased, I don't need it anymore. The thing is I can't do anything with it. And no, the disk is not full, see attached picture.

---

### Post by DeMus on 2011-04-05
Using gnome-disk-utility I can unmount the "drive" but when I format the drive I get this:
```
Error creating partition table: helper exited with exit code 1: Error calling fsync(2) on /dev/sdd: Input/output error
```

When I format the volume I get this:
```
Error creating file system: helper exited with exit code 1: Error calling fsync(2) on /dev/sdd1: Input/output error
```

When trying to delete the partition I get:
```
Error erasing: helper exited with exit code 1: In part_del_partition: device_file=/dev/sdd, offset=32256
Entering MS-DOS parser (offset=0, size=1031798784)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 1031766528, type 0x06)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
got it
got disk
got partition - part->type=0
Error: Input/output error during write on /dev/sdd
Warning: Error fsyncing/closing /dev/sdd: Input/output error
ped_disk_commit_to_dev() failed

```

Anyone any idea what is going on with my USB-stick and what I can do about it? I have no idea.

Edit:
I used Gparted to delete the partition and I got this as error message:

```
GParted 0.5.1

Libparted 2.2

Delete /dev/sdd1 (fat16, 983.97 MiB) from /dev/sdd  00:00:00    ( ERROR )
    	
calibrate /dev/sdd1  00:00:00    ( SUCCESS )
    	
path: /dev/sdd1
start: 63
end: 2015231
size: 2015169 (983.97 MiB)
delete partition  00:00:00    ( ERROR )
libparted messages    ( INFO )
    	
Input/output error during write on /dev/sdd
Error fsyncing/closing /dev/sdd: Input/output error

```

---

### Post by Rebelli0us on 2011-04-05
Can you delete files in Windows? If not maybe the flash drive is defective. 1GB stick is worth maybe $4, I'd replace it.

---

### Post by DeMus on 2011-04-05
> **Rebelli0us said:**
> Can you delete files in Windows? If not maybe the flash drive is defective. 1GB stick is worth maybe $4, I'd replace it.

Yes, I was thinking the same thing. But I started this thread to find out what happened and if there was a solution possible. Buying a new one is the easy way out, although it is starting to look like it is the only way out.
Anybody any idea before I go out and get me a new one?

---

### Post by blueridgedog on 2011-04-05
Try with fdisk (while unmounted):

```
sudo fdisk /dev/sdd
```

Then:

Type "m" to get a list of commands...read through them to familiarize yourself with them.

Type "p" to print the partition table...you should see only sdd1. Make certain you only see your expected partition as if you typed the wrong disk name at the start, the next step would be unrecoverable should it delete a partition you really wanted to keep.

Type "d" to delete a partition...you should get a message that one partition was selected.

Type "w" to write the partition table you just created (an empty one).

Go back into fdisk...

Type "p" to print the partition table...it should be empty

Type "n" to add a partition.

Type "p" for primary, then 1 for first partition, then take the defaults for start and end.

Type "t" to toggle the partition type then "L" to list the codes, then "b" for FAT32.

Type "w" to write the new table.

If the partition is created, you can try and format it with:

```
sudo mkfs.vfat /dev/sdd1
```

Again...make certain you specify the right device and partition.

The disk may be bad, but fdisk may salvage it.

---

### Post by DeMus on 2011-04-05
Thank you very much for your help blueridgedog, but .....
Directly at the start of the program it says:
```
You will not be able to write the partition table
```
When I type w for writing the new partition table I get the message:
```
Unable to write to /dev/sdd
```

The disk is read-only and I have no way of changing that.
I just tried it again in Windows and I get the exact same results: I can not write to a read-only device.


I really hope you have some ideas how to get rid of the read-only flag.

---

### Post by DeMus on 2011-04-05
What could also be interesting is this:

Using p in fdisk I get:

Device     Boot  Start     End    Blocks    Id  System
/dev/sdb1    *       1     126    1007584+   6  FAT16
Partition 1 has different physical/logical endings:
    phys=(124, 254, 63)  logical=(125, 112, 51)

Does this help in any way?

---

### Post by Dutch70 on 2011-04-05
See if you can check the usb stick with Disk Utility. 

Also, this is kinna out there, but so is your problem ;)
Try opening Startup Disk Creator and see if you can erase the disk.

---

### Post by DeMus on 2011-04-05
> **Dutch70 said:**
> See if you can check the usb stick with Disk Utility. 

Also, this is kinna out there, but so is your problem ;)
Try opening Startup Disk Creator and see if you can erase the disk.

Hi,
Startup Disk Creator gave me this:
```
org.freedesktop.UDisks.Error.Failed: Error creating partition table: helper exited with exit code 1: Error calling fsync(2) on /dev/sdd: Input/output error
```

I'm pretty sure the stick is broken somehow and it's not a software thing, unless somebody has some idea how to get rid of the read-only flag and the input/output error.

Anyway, thank you all for trying to help me.

---

### Post by Dutch70 on 2011-04-05
Yeah, sounds like it might have seen it's last days.

---

### Post by oldfred on 2011-04-05
What if you totally zeroout the MBR & partition table.

This command is very dangerous as it uses dd also know as Data Destroyer. So make sure your flash is still sdd or you will destroy one of your other drives.


Zero out MBR and partition table
dd if=/dev/zero of=/dev/[COLOR=Red]sdd[/COLOR] bs=512 count=1

Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement](https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement)

---

### Post by DeMus on 2011-04-05
> **oldfred said:**
> What if you totally zeroout the MBR & partition table.

This command is very dangerous as it uses dd also know as Data Destroyer. So make sure your flash is still sdd or you will destroy one of your other drives.


Zero out MBR and partition table
dd if=/dev/zero of=/dev/[COLOR=Red]sdd[/COLOR] bs=512 count=1

Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement](https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement)

Thanks for you help, but even dd gets the message the drive is read-only. So I can not write anything to it.
I give up. Thanks all of you for trying to help, I will get me a new one and hope that one will last longer.

---

