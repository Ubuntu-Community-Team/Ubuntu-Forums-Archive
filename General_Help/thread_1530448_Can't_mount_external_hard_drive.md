---
title: "Can't mount external hard drive"
date: 2010-07-13
forum: General Help
---

### Post by JustSteph on 2010-07-13
I'm having problems getting Ubuntu 10.4 to detect my external hard drive. No idea why, since it worked perfectly yesterday and I disconnected it properly. This is what I've done so far:

```
steph@steph-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 029: ID 0bc2:2300 Seagate RSS LLC 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
``````
steph@steph-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5874    47182873+   7  HPFS/NTFS
/dev/sda2           16709       19458    22082561    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3            5875       15600    78124095    7  HPFS/NTFS
/dev/sda5           16709       19338    21120117+  83  Linux
/dev/sda6           19338       19458      961536   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
1 heads, 63 sectors/track, 9922896 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x023f62b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2     9922816   312568672+   7  HPFS/NTFS
```So it's detecting it, but when I try to mount it, I get this:

```
steph@steph-laptop:~$ sudo mkdir /media/320
steph@steph-laptop:~$ sudo mount -t ntfs /dev/sdb1/ /media/320
Error reading bootsector: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```

But it isn't Windows I'm having the problem with.

Any help would be greatly appreciated. Thanks.

---

### Post by ElevenWarrior on 2010-07-13
Well, the error its giving is saying that the file system, MAY be corrupt, or your using a Raid device, I'd take these steps, and seem if they help
1. Post the excat model of your external HD, and the model of the computer your running ubuntu on.
2. Can you mount the drive in windows?
 2.a If you can have you tried running chkdsk /f?
3. Google your problem
see if anyone else is getting the error your getting.
 (perhaps check out the dmraid documentation as it says to?)
sorry if its not much help.

---

### Post by JustSteph on 2010-07-13
Thanks for your reply.

I'm running Ubuntu on an Acer 5920, and my external HD is a Seagate 320Gb

I'm on Windows now, and I can access it, but it looks like it's completely empty. Really hoping it isn't, since I had data on there I don't have anywhere else.

I haven't run chkdsk /f yet, I'll do it in a minute.

I've already googled it and didn't find anything useful.

I don't know what the dmraid documentation is =S

---

### Post by JustSteph on 2010-07-13
I ran chkdsk /f and now it wont mount on Windows either.

---

### Post by nothingspecial on 2010-07-13
I`ve no idea if this will help

plug it back into ubuntu but unmount it

```
sudo apt-get install ntfsprogs
```
```

sudo fdisk -l
```

to determine the /dev/sd?? it has been assigned
```

sudo ntfsfix /dev/sd??
```

Again, make sure the drive has not mounted (I realise this is the problem)

From the man page
```

ntfsfix is a utility that fixes some common NTFS problems. ntfsfix is NOT a Linux version of chkdsk.   It only repairs some fundamental NTFS inconsistencies, resets the NTFS journal file and schedules an NTFS consistency check for the first boot into Windows.  You may run ntfsfix on an NTFS volume if you think it was damaged by  Windows or some other way  and it cannot be mounted.  

```

Again, no idea if this will help.

---

### Post by JustSteph on 2010-07-13
Thank you. I did that and got:

```
steph@steph-laptop:~$ sudo ntfsfix /dev/sdb
Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.
```

I already ran chkdsk and it didn't help =S

---

### Post by nothingspecial on 2010-07-13
Well in that case this will probably not help but try it with the number, as in /dev/sdb is the drive, but /dev/sdb1 (or /dev/sdb2, or /dev/sdb3) is the partition.

Again, I have never used a ntfs drive and don`t have one so I have no idea if this will help or harm the situation. All I do know is that they say in the documentation to make sure the drive is not mounted.

---

### Post by JustSteph on 2010-07-13
With the number, it says "Mounting volume..." but doesn't appear to do anything else.

EDIT: It eventually did:
```
steph@steph-laptop:~$ sudo ntfsfix /dev/sdb1
Mounting volume... Error reading bootsector: Input/output error.
Failed to startup volume: Input/output error.
FAILED
Attempting to correct errors... Error opening partition device: No such file or directory.
FAILED
Failed to startup volume: No such file or directory.
Volume is corrupt. You should run chkdsk.

```

---

### Post by ezsit on 2010-07-13
Found this article on MS's site, maybe it could help:

[http://support.microsoft.com/kb/121517](http://support.microsoft.com/kb/121517)

You will need Norton Utilities to proceed.

---

### Post by mr clark25 on 2010-07-13
could you run something like "fsck /dev/sdb1"?

wait for someone to confirm that this will work.

---

### Post by JustSteph on 2010-07-16
I don't know if this will help any, but under "Properties" (on Windows) for the drive, it says that there is 0 bytes of used space, 0 bytes of available space, 0 bytes capacity and that the file system is RAW. I've tried formatting it, but I click "Format" and nothing happens. The same is true when I try to check for errors.

In Ubuntu, Disk Utility doesn't detect the drive so I can't format there. Is there a way I can format from the Terminal?

---

### Post by JustSteph on 2010-07-16
bump?

---

### Post by nothingspecial on 2010-07-16
> **JustSteph said:**
> Is there a way I can format from the Terminal?
```

sudo mkfs -t ext3 /dev/sdb1
```

Assuming this is what fdisk still identifies it as.

---

### Post by JustSteph on 2010-07-16
Thank you.

I don't think it worked though. I still can't access it.
```
mke2fs 1.41.11 (14-Mar-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
19537920 inodes, 78142168 blocks
3907108 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
2385 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616

Writing inode tables: done                            
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir
```

---

### Post by nothingspecial on 2010-07-16
> **JustSteph said:**
> 

In Ubuntu, Disk Utility doesn't detect the drive so I can't format  there. Is there a way I can format from the Terminal?

I`m assuming you don`t care about the data on there

Right.....

Make sure you get this exactly right. Make sure sdb is the disk in question. Please.

```
sudo fdisk /dev/sdb
```

Then press m to see the options

press o (to create a new partition table)

press n (to add a new partition)

press p (to make it a primary partition)

I think 1 is the best option next

Then press w to save and exit

Then
```

sudo mkfs -t ext4 /dev/sdb1
```

If that doesn`t work I`m out of ideas.

Do me a favour, have a look at the options for fdisk and make sure I`ve got this right - (the kids are fighting and doing my head in [-X) 

I don`t want to make this worse because I`m distracted.

---

### Post by JustSteph on 2010-07-16
Thanks. I appreciate your help.

I tried formatting it to NTFS instead and got this:
```
steph@steph-laptop:~$ sudo mkfs -t ntfs /dev/sdb1
Cluster size has been automatically set to 4096 bytes.
Initializing device with zeroes: 100% - Done.
Creating NTFS volume structures.
Error writing to /dev/sdb1: Input/output error.
Error writing non-resident attribute value.
add_attr_sd failed: Input/output error
Couldn't create root directory: Input/output error
```

Doing what you suggested, I get told "Unable to write /dev/sdb" after w to save and exit.

---

### Post by nothingspecial on 2010-07-16
Steph, I`m out of ideas.

Good luck.

---

### Post by JustSteph on 2010-07-16
Thanks for your help :)

---

