---
title: "quick format a usb drive?"
date: 2012-10-03
forum: General Help
---

### Post by sohlinux on 2012-10-03
Is there a quick way of formatting a 2tb usb drive?

I ran the following command a couple of hours ago and its still less than half way through...

mkfs.ext3 /dev/sde

thanks

---

### Post by sdpagent on 2012-10-03
A format should only take a few minutes I think as you are not actually overwriting the entire drive. A secure erase or shred operation should take hours though.

Have you tried doing a search of your system for 'disks' there is a nice gui tool there for formatting drives etc. If you are using unity or latest gnome interface all you have to do is hit the 'super' or 'windows' key and type 'disk' and it should be the first result.

Hope I was of some help.

Stu

---

### Post by sohlinux on 2012-10-03
thanks but in this case I only have access to that drive via the command line, was wondering if there was a quick format command but I cannot find one.

---

### Post by coldraven on 2012-10-03
Did you unmount it first?

---

### Post by sohlinux on 2012-10-03
> **coldraven said:**
> Did you unmount it first?

it wasnt mounted, its a new raw drive

here is what it says

fdisk -l
Disk /dev/sde: 2000.3 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sde doesn't contain a valid partition table

root@server [/]# mkfs.ext3 /dev/sde
mke2fs 1.39 (29-May-2006)
/dev/sde is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
244203520 inodes, 488378646 blocks
24418932 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
14905 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000, 214990848

Writing inode tables: 12189/14905

as you can see its 3/4 way through now but the total time is going to be 4 hours plus!

---

### Post by Cheesemill on 2012-10-03
You shouldn't be creating a filesystem on sde (the entire drive). Instead you should first create a partition table and then a partition using either fdisk or parted and then create the filesystem on top of the partition.

I don't believe that what you are doing will even work.

---

### Post by sohlinux on 2012-10-03
> **Cheesemill said:**
> You shouldn't be creating a filesystem on sde (the entire drive). Instead you should first create a partition table and then a partition using either fdisk or parted and then create the filesystem on top of the partition.

I don't believe that what you are doing will even work.

your right, I forgot to create a partition
fdisk /dev/sde

---

### Post by sohlinux on 2012-10-03
for the last half hour after starting the partition writing it still says calling ioctl() to re-read partition table

how long does that usually take?

---

### Post by Cheesemill on 2012-10-03
I don't know, I've never tried creating a filesystem on an entire drive as it's not the correct way to do things (as I mentioned earlier I don't think you'll end up with a usable drive anyway).

Last time I formatted my 1GB external with ext4 the whole process took about 30 seconds.

Your best bet would be to quit the current operation and start again using the correct method. If you are unsure what you are doing you could always boot from a Live CD and use Gparted to do the whole lot for you.

---

### Post by sohlinux on 2012-10-03
> **Cheesemill said:**
> I don't know, I've never tried creating a filesystem on an entire drive as it's not the correct way to do things (as I mentioned earlier I don't think you'll end up with a usable drive anyway).

Last time I formatted my 1GB external with ext4 the whole process took about 30 seconds.

Your best bet would be to quit the current operation and start again using the correct method. If you are unsure what you are doing you could always boot from a Live CD and use Gparted to do the whole lot for you.

I did start again by first creating a partition with fdisk /dev/sde

now its hanging on "calling ioctl() to re-read partition table"

I cant boot with a cd because its a remote box

fdisk /dev/sde

Enter n to create a new partition

n

Enter 1 to select partition

1 

accept default start and end

Type w to write and exit

w

at this point its hanging on "calling ioctl() to re-read partition table"

Next job (if it gives me the chance) is to assign a File system to the hard drive with the following command.

mkfs.ext3 /dev/sde

---

### Post by Cheesemill on 2012-10-03
> I did start again by first creating a partition with fdisk /dev/sde
There is something funny going on here, can I take a look at your partition table.
What is the output of:
```
sudo fdisk -l /dev/sde
```

---

### Post by sohlinux on 2012-10-03
> **Cheesemill said:**
> [QOUTE]I did start again by first creating a partition with fdisk /dev/sde
There is something funny going on here, can I take a look at your partition table.
What is the output of:
```
sudo fdisk -l /dev/sde
```[/QUOTE]


Disk /dev/sde: 2000.3 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

---

### Post by Cheesemill on 2012-10-03
You still haven't created a partition.

The easiest way to do this is with fdisk, first do:
```
sudo fdisk /dev/sde
```
Then do the following:
o   (to create a new partition table)
n   (to create a new partition)
Enter x 4 (to use default options)
w   (to write partition table to disk and exit)

Then can you post the output of fdisk again please:
```
sudo fdisk -l /dev/sde
```

---

### Post by sohlinux on 2012-10-03
> **Cheesemill said:**
> You still haven't created a partition.

The easiest way to do this is with fdisk, first do:
```
sudo fdisk /dev/sde
```
Then do the following:
o   (to create a new partition table)
n   (to create a new partition)
Enter x 4 (to use default options)
w   (to write partition table to disk and exit)

Then can you post the output of fdisk again please:
```
sudo fdisk -l /dev/sde
```

I did exactly that but its hanging on "calling ioctl() to re-read partition table"

---

### Post by sohlinux on 2012-10-03
I rebooted the server and it now fine, not sure what the problem was but its sorted :) thanks

---

