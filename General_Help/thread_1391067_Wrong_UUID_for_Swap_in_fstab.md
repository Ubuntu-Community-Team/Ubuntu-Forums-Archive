---
title: "Wrong UUID for Swap in fstab"
date: 2010-01-26
forum: General Help
---

### Post by LordKelvan on 2010-01-26
Hi:

I've recently started having some problems with my swap partition.  When I start up my computer, often I get an error message that says Ubuntu couldn't mount the swap partition.  After logging in, everything is fine except swap is not present.  Checking the directory /dev/disk/by-uuid, I notice that my swap's UUID (as it is in /etc/fstab) is not present.  The output of the command
```

cat /etc/initramfs-tools/conf.d/resume
```
matches swap's UUID in /etc/fstab.  However, the output of 
```

sudo blkid
```
does not list a UUID for my swap partition, and GParted also does not show a UUID when I look under the properties of the swap partition.  Anyone know why this is happening?

Right now, I've changed /etc/fstab to use the device path (i.e., /dev/sdc7) for the swap partition, and it seems to be working.  What is the difference between using a UUID versus a path to identify a partition?  Is it that a UUID will never change, whereas a device path could under some circumstances?  Is it possible that by changing the physical set-up of my drives (add, remove, plug into different motherboard SATA connector), /dev/sdc7 could come to point to a partition which I don't intend to be used for swap, causing data loss?

Cheers,
LK

---

### Post by plucky on 2010-01-26
Post output of ```
sudo fdisk -l
sudo blkid -c /dev/null
```

> Is it possible that by changing the physical set-up of my drives (add, remove, plug into different motherboard SATA connector), /dev/sdc7 could come to point to a partition which I don't intend to be used for swap, causing data loss?


Very unlikely as the swap partition uses a different format to a normal ext3/ext4 partition and this is specified in the /etc/fstab file.The partition will just not mount.

---

### Post by ibuclaw on 2010-01-26
Perhaps you should try reformatting the swap partition then and update all configuration files to match the new UUID?

---

### Post by LordKelvan on 2010-01-28
Relevant output of "fdisk -l":

```

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
16 heads, 63 sectors/track, 486344 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xec6e2106

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      208415   105041128+   7  HPFS/NTFS
/dev/sdc2          208416      486344   140076216    5  Extended
/dev/sdc5          208431      435939   114663937+  83  Linux
/dev/sdc6          435953      485327    24884968+  83  Linux
/dev/sdc7          485328      486344      512536+  82  Linux swap / Solaris

```

Relevant output of "blkid -c /dev/null":

```

/dev/sdc7: TYPE="swap"

```

As for formatting the swap partition, I'm not sure what that means.  Do you mean I should recreate the partition using GParted (or some equivalent program)?

---

### Post by john newbuntu on 2010-01-29
Yeah as Tinivole suggested, you may have to reformat your swap partition, which would then enable "sudo blkid" to show the right UUID.  My guess is that you have adjusted a partition or two, causing the UUID to change.  UUIDs are assigned when the filesystem is created.  On the other hand, device names are determined at creation/discovery time.

The /etc/initramfs-tools/conf.d/resume file, I am guessing is created at install time and so is outdated.

The following steps create and enable swap:
```
sudo swapoff -a
sudo /sbin/mkswap /dev/sdc7
//Now edit fstab to add the UUID given in the above step.
sudo swapon -a
//Finally check
swapon -s
sudo blkid

```
Ignore my C style comments in the above code block.

---

### Post by hawthornso23 on 2010-01-29
> **tinivole said:**
> Perhaps you should try reformatting the swap partition then and update all configuration files to match the new UUID?

Make sure you back up your swap partition first ... ... ...:lolflag:

---

### Post by LordKelvan on 2010-02-01
john/Tinivole:  I followed the specified steps, and my swap partition has a UUID again.  What was weird was that my swap partition previously lacked a UUID (it wasn't that it had the wrong one).  Thanks.

---

### Post by vanadium on 2010-02-02
It came to my attention that my swap is announced with the device name, and not with the UUID, in /etc/fstab. Moreover, the swap partition does not have an UUID as shown by the "sudo blkid" command.

This is an freshly installed 9.10 system on a laptop. Thus, it would seem that on Karmic Koala, swap is by default mounted by a device name, and not by an UUID. At least, that is what happened on my system.

I am sure that UUIDS were used for swap in previous versions of Ubuntu.

---

### Post by toineurlings on 2010-02-23
> **john newbuntu said:**
> Yeah as Tinivole suggested, you may have to reformat your swap partition, which would then enable "sudo blkid" to show the right UUID.  My guess is that you have adjusted a partition or two, causing the UUID to change.  UUIDs are assigned when the filesystem is created.  On the other hand, device names are determined at creation/discovery time.

The /etc/initramfs-tools/conf.d/resume file, I am guessing is created at install time and so is outdated.

The following steps create and enable swap:
```
sudo swapoff -a
sudo /sbin/mkswap /dev/sdc7
//Now edit fstab to add the UUID given in the above step.
sudo swapon -a
//Finally check
swapon -s
sudo blkid

```
Ignore my C style comments in the above code block.

When I put in this code I get this output (without solving the problem):
```
toineurlings@pc-onder:~$ sudo swapoff -a
toineurlings@pc-onder:~$ sudo /sbin/mkswap /dev/sdc7
/dev/sdc7: Bestand of map bestaat niet
toineurlings@pc-onder:~$ //Now edit fstab to add the UUID given in the above step.
bash: //Now: Bestand of map bestaat niet
toineurlings@pc-onder:~$ sudo swapon -a
swapon: cannot find the device for UUID=7e42129b-a71e-4cc7-b56b-7dbe78a73fb1
toineurlings@pc-onder:~$ //Finally check
bash: //Finally: Bestand of map bestaat niet
toineurlings@pc-onder:~$ swapon -s
Filename				Type		Size	Used	Priority
toineurlings@pc-onder:~$ sudo blkid
/dev/sda1: UUID="1b0f8e2b-4dbb-4180-9ff1-d5f1b7807c6f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: LABEL="SWAP" UUID="d9386759-dfc7-4818-94bf-1ab7095e8484" TYPE="swap" 
toineurlings@pc-onder:~$ 

```

---

### Post by bodhi.zazen on 2010-02-23
See this link for further details :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

List your partitions with blkid:

```
sudo blkid
```

Now open /etc/fstab and edit the line for swap

```
gksu gedit /etc/fstab
```

UUID=xyz swap ....

Add the UUID from the blkid command 

If you do not understand how to do this, post the output of the blkid command and the contents of /etc/fstab

Then, save /etc/fstab and

```
sudo swapon
```

---

### Post by OzzyFrank on 2010-12-14
> **hawthornso23 said:**
> Make sure you back up your swap partition first ... ... ...:lolflag:

Funny.

But seriously, I found the info about **sudo /sbin/mkswap /dev/sd##** very useful! I used to format the swap etc when it lost its UUID, but that command saves the hassle.

---

