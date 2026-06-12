---
title: "Partition Problem..."
date: 2010-03-27
forum: General Help
---

### Post by madmax.santana on 2010-03-27
I want to change my sda2 partition to ntfs type. i have installed GParted but it is returning a strange type of error.

Here is the error dump file...

> GParted 0.5.1

Libparted 2.2
Format /dev/sda2 as ntfs  00:00:04    ( ERROR )
     	
calibrate /dev/sda2  00:00:00    ( SUCCESS )
     	
path: /dev/sda2
start: 89996130
end: 136295459
size: 46299330 (22.08 GiB)
set partition type on /dev/sda2  00:00:04    ( ERROR )
libparted messages    ( INFO )
     	
WARNING: the kernel failed to re-read the partition table on /dev/sda (Device or resource busy). As a result, it may not reflect all of your changes until after reboot.
WARNING: the kernel failed to re-read the partition table on /dev/sda (Device or resource busy). As a result, it may not reflect all of your changes until after reboot.

I have tried rebooting and doing the same again... But to no avail. Please help.

---

### Post by srs5694 on 2010-03-27
It's unclear what commands you're giving to libparted. I recommend you go for lower-level utilities:


[list=1]
[*]Type "sudo fdisk /dev/sda" to launch fdisk.
[*]Type "p" to see the partition table and verify that you're working on the correct disk.
[*]Type "t" to change the partition type code. Enter the partition number and a type code of "07" when prompted.
[*]Type "p" to see the partition table and verify that you've changed the type of the correct partition. If not, type "q" to exit without saving changes and try again.
[*]If your partition table looks correct, type "w" to write the changes and exit.
[*]Type "sudo mkfs.ntfs -f /dev/sda2" to turn /dev/sda2 into an NTFS partition.
[/list]


If something strange or unexpected happens at any of these steps, post back with details.

---

### Post by Mark Phelps on 2010-03-27
Another possibility is that, since you're running GParted from inside Ubuntu, you have the sda2 partition already mounted.

You can't work on a mounted partition.  If you unmount it, you should be able to then work on it.

Also, the partition is empty, right? Because if not, any conversion will most likely erase the contents.

---

### Post by gordintoronto on 2010-03-27
Could you Alt-Prt Scr to capture Gparted's view of your partition table, then attach the image here?

If sda2 is an extended partition, it would *contain* partitions which could be set to NTFS, beginning with sda5.

---

### Post by madmax.santana on 2010-03-27
It should be no problem since I have been doing the same under Jaunty and Interpid.

And no, as you can see, it is not mounted, rather it won't mount because it says "could not determine fstype of /dev/sda2"

And yes! It is empty. How would I store data o "unallocated space" or "unknown filesystem"... :P

Here are the requested screenshots.

---

### Post by madmax.santana on 2010-03-27
> **srs5694 said:**
> It's unclear what commands you're giving to libparted. I recommend you go for lower-level utilities:


[list=1]
[*]Type "sudo fdisk /dev/sda" to launch fdisk.
[*]Type "p" to see the partition table and verify that you're working on the correct disk.
[*]Type "t" to change the partition type code. Enter the partition number and a type code of "07" when prompted.
[*]Type "p" to see the partition table and verify that you've changed the type of the correct partition. If not, type "q" to exit without saving changes and try again.
[*]If your partition table looks correct, type "w" to write the changes and exit.
[*]Type "sudo mkfs.ntfs -f /dev/sda2" to turn /dev/sda2 into an NTFS partition.
[/list]


If something strange or unexpected happens at any of these steps, post back with details.
This is the result of the whole operation...
> 
Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)
Syncing disks.
Of course it didn't get to using mkfs.ntfs, since the step 5 did not complete successfully... What do yeh recommend now?

---

### Post by jawilljr on 2010-03-27
> **madmax.santana said:**
> This is the result of the whole operation...

Of course it didn't get to using mkfs.ntfs, since the step 5 did not complete successfully... What do yeh recommend now?

Use the partprobe command:

```
sudo partprobe
```Then format to ntfs.

More information [U][Here.]("http://www.cyberciti.biz/tips/re-read-the-partition-table-without-rebooting-linux-system.html")


[ ]("http://www.cyberciti.biz/tips/re-read-the-partition-table-without-rebooting-linux-system.html")[/U]

---

### Post by srs5694 on 2010-03-27
> **madmax.santana said:**
> This is the result of the whole operation...

Of course it didn't get to using mkfs.ntfs, since the step 5 did not complete successfully... What do yeh recommend now?

Actually, the operation *did* complete successfully. The message you report isn't an error; it's just that the kernel doesn't recognize the changes you made. Since you didn't change any partitions' locations, just their type codes, you should be able to continue with running mkfs.ntfs. If you're in doubt, try running fdisk again and check that the partition type code has actually changed on disk.

---

### Post by psusi on 2010-03-28
You can not use gparted fully on a disk that has ANY mounted partitions.  You need to run it from the livecd so you aren't using the disk.

---

### Post by jawilljr on 2010-03-28
> **srs5694 said:**
> Actually, the operation *did* complete successfully. The message you report isn't an error; it's just that the kernel doesn't recognize the changes you made. Since you didn't change any partitions' locations, just their type codes, you should be able to continue with running mkfs.ntfs. If you're in doubt, try running fdisk again and check that the partition type code has actually changed on disk.

I agree with you.. the kernel doesn't recogize the changes, so the OP has to do one of the following after step 5:

  1. Reboot or
  2.  Execute the command 'partprobe' (as root)

Either one will tell the kernel the changes to the partition table

Then format the partition to NTFS

Jerry

---

### Post by srs5694 on 2010-03-28
> **jawilljr said:**
> I agree with you.. the kernel doesn't recogize the changes, so the OP has to do one of the following after step 5:

  1. Reboot or
  2.  Execute the command 'partprobe' (as root)

Either one will tell the kernel the changes to the partition table

Then format the partition to NTFS


Doing this will do no harm, but neither is it necessary in this case. So long as the partition start point, end point, and number don't change, creating a new filesystem on a partition after you change its type code is perfectly safe.

---

### Post by jawilljr on 2010-03-28
> **srs5694 said:**
> Doing this will do no harm, but neither is it necessary in this case. So long as the partition start point, end point, and number don't change, creating a new filesystem on a partition after you change its type code is perfectly safe.

Read the below error message from post #6:

> Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table. The new table will be used at
the next **reboot** or after you run **partprobe**(:cool: or kpartx(:cool:
Syncing disks.                      Fdisk is telling him to either reboot or run partprobe... then format.  so in my opinion it is necessary.

Jerry

---

### Post by srs5694 on 2010-03-28
> **jawilljr said:**
> Read the below error message from post #6:

Fdisk is telling him to either reboot or run partprobe... then format.  so in my opinion it is necessary.

It's not. Trust me. I've written Linux partitioning software ([GPT fdisk,](http://www.rodsbooks.com/gdisk/) to be precise), and I understand what's going on here. The kernel is not using the new partition table, but it is using the old one. Since the only difference between the old and new partition tables is the type code, which Linux doesn't use, there's no need to reboot.

That said, rebooting won't do any harm, and there *are* changes that would make creating a new filesystem dangerous after making a partition table change. For instance, if you change the start or end point of a partition or change the number of the partition. Thus, if you don't know what you're doing or if there's doubt in your mind, it's certainly safer to reboot. In *this specific case,* though, that's not necessary.

---

### Post by jawilljr on 2010-03-28
> **srs5694 said:**
> It's not. Trust me. I've written Linux partitioning software ([GPT fdisk,]("http://www.rodsbooks.com/gdisk/") to be precise), and I understand what's going on here. The kernel is not using the new partition table, but it is using the old one. Since the only difference between the old and new partition tables is the type code, which Linux doesn't use, there's no need to reboot.

That said, rebooting won't do any harm, and there *are* changes that would make creating a new filesystem dangerous after making a partition table change. For instance, if you change the start or end point of a partition or change the number of the partition. Thus, if you don't know what you're doing or if there's doubt in your mind, it's certainly safer to reboot. In *this specific case,* though, that's not necessary.

All I am going on is fdisk's error message... it is telling him to either reboot or run partprobe... so *something* has changed.

Jerry

---

### Post by srs5694 on 2010-03-28
> **jawilljr said:**
> All I am going on is fdisk's error message... it is telling him to either reboot or run partprobe... so *something* has changed.

First, it's not an error message. It's a warning message. The message doesn't even say what you're claiming -- namely, it does not "tell.. him to... reboot;" it tells him that the "...new table will be used at the next reboot...".

Second, and more importantly, you've just made my point. You're going on the program's English-language text messages, which are imprecise and open to interpretation. (That's not an indictment of the fdisk authors; it's a comment on the nature of human language compared to computer programming languages.) I'm going on the source code and a much deeper understanding of the issues involved, which enable me to say with certainty that *in this instance,* no reboot is required, provided my instructions are followed precisely.

---

### Post by madmax.santana on 2010-03-28
> **srs5694 said:**
> Actually, the operation *did* complete successfully. The message you report isn't an error; it's just that the kernel doesn't recognize the changes you made. Since you didn't change any partitions' locations, just their type codes, you should be able to continue with running mkfs.ntfs. If you're in doubt, try running fdisk again and check that the partition type code has actually changed on disk.
Yeah, that is the case most probably. Since:
I executed mkfs.ntfs after changing the partition code using fdisk and it was all fine. No reboot or partition probing needed. Thanks all.

---

