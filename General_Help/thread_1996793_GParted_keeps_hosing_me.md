---
title: "GParted keeps hosing me"
date: 2012-06-04
forum: General Help
---

### Post by gmoore777 on 2012-06-04
( so twice in 2 days, GParted has not left my partition/filesystem
in good shape.
The first time, i'm not sure how I fixed it. It seemed
running GParted and increasing the recently decreased partition size
rectified itself but this is what I did today with gparted.
)

I have several partitions on my one hard drive.

I have LucidLynx on /dev/sda5 and on a following, adjacent partition,
/dev/sda8, I have a recently installed (yesterday) PrecisePangolin
installation.

Today, I wanted to shrink /dev/sda5 by 4 GB and give it to /dev/sda8
using GParted.

I booted up PrecisePangolin, on /dev/sda8, and
using GParted, I shrank /dev/sda5 by 4 GB, and applied the changes.
Rebooted.
Chose from Grub to boot up /dev/sda5.
That failed, I got kicked out to that intraramfs prompt, or something like that.

I then boot up my PrecisePangolin, and tried to mount /dev/sda5, I get
this from `dmesg`:
    EXT4-fs (sda5): bad geometry: 
          block count 3586958 exceeds size of device (2560142 blocks)

With 4096 byte blocks, "3586958" represents the old size of /dev/sda5 of 14 GB, and "2560142" represents the new smaller size of /dev/sda5 at 10 GB.

So GParted, altered something correctly, the MBR, I imagine,
 cause `sudo fdisk -l` shows the correct resized entry:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda5         4289418    24770559    10240571   83  Linux

(this is shown in 1024 byte size blocks: "10240571" = 10 GB)

I've Googled around, and there seems to be no clear answer on how to
fix this and it does appear to be close to rocket science.

Here are a few commands that I tried:

$ sudo resize2fs -f /dev/sda5
resize2fs 1.42 (29-Nov-2011)
Resizing the filesystem on /dev/sda5 to 2560142 (4k) blocks.
resize2fs: Can't read an block bitmap while trying to resize /dev/sda5
Please run 'e2fsck -fy /dev/sda5' to fix the filesystem
after the aborted resize operation.
$

$ sudo e2fsck -f /dev/sda5
e2fsck 1.42 (29-Nov-2011)
The filesystem size (according to the superblock) is 3586958 blocks
The physical size of the device is 2560142 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? yes
$

Help!

---

### Post by wilee-nilee on 2012-06-04
You're making some mistake here, hard to tell where, gparted has worked fine here in the over 1000 times I have used it. 

You just have to know what the tools can and can not do.

When you say you don&#8217;t know how you fixed it it seems you have some confusion. ;)

No boot flag is needed to boot linux.

---

### Post by gmoore777 on 2012-06-04
in the 1000 times you have used gparted, did you ever use gparted
from either a PrecisePangolin LiveCD, or from a booted 
PrecisePangolin partition, whereas you "shrunk" a LucidLynx partition?

All I did both times was run GParted, selected /dev/sda5 and
chose resize/move, and made the size smaller, applied changes,
exit. That's all. No confusion here.
The confusion I have is that it didn't work.

In either case, I'm looking for assistance on how to fix this,
not general ramblings.

---

### Post by ajgreeny on 2012-06-04
If you have sda5 and sda8 on a disk they are both logical partitions within an extended partition, so in theory you should not have been able to make any changes to either partition while running gparted from the other partition.

If you did manage to do that by some means or other, it may well explain why you are now seeing error messages on one or both of those partitions.  More details may help us sort out things for you, but I do haver severe doubts, I'm afraid.

For safety's sake I would recommend that to use gparted on anything other than perhaps an external disk's partitions, you should boot to a live CD (Gparted live, or of course Ubuntu live CD).  Having said all this, I am extremely amazed that you even werev allowed to do what you say you did; gparted would normally refuse to act in those circumstances.

Unfortunately I have no idea how to fix your problems, but thought it worth making these comments for future reference.

---

### Post by gmoore777 on 2012-06-04
Here are the details of my drive via `fdisk -l` with
a few rows rearranged and a slot where the 4 GB of freed
space is sitting:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      192779       96358+  de  Dell Utility
/dev/sda2   *      192780     4289354     2048287+  83  Linux
/dev/sda3         4289416   625141759   310426172    5  Extended
/dev/sda5         4289418    24770559    10240571   83  Linux
< there is 4 GB unallocated space between these 2 partitions >
/dev/sda8        32987136    86204415    26608640   83  Linux
/dev/sda7        86212608   592365567   253076480   8e  Linux LVM
/dev/sda6       592373760   625141759    16384000   82  Linux swap

sda2 is a 2 GB Grub-only partition
sda3 is a 310 GB extended partition
sda5 is my 10 GB LucidLynx partition (shrunk for a second time)
Then there is 4 gb free space that was just stolen from sda5.
sda8 is my new 26 GB PrecisePangolin installation.
    This 26 GB was previously stolen/created via shrinking sda5 yesterday.
sda7 is a 250 GB LVM partition housing Xen dom0 and domU installations.
sda6 is the 16 GB swap space

Yesterday, sda5 was 40 GB.
I shrunk that to 14 GB, then created sda8 with the 26 GB that
was freed.
After installing PrecisePangolin on sda8, I then wanted to 
steal 4 more GB from sda5. (yes, I was greedy)
That's where I'm stuck currently.

Assuming the information in the MBR (fdisk -l) is correct, which I believe it is, isn't there a command to write/fix the superblock sitting in 
/dev/sda5 to tell it the file system ( on sda5) is the same size as the 
sda5 partition (10 GB), so that `e2fsck` has a better chance of succeeding.
(by the way, I understand the MBR, but I really don't know what the
superblock is, or how naively simple it is to edit.)

In regards to ajgreeny, technically, it makes sense to me that gparted
could make changes to partitions as members of an extended partition.
Lets say one still had 100 GB of unallocated space inside an extended 
partition. GParted is the tool that one would use to say, create 4 more
25 GB partitions. Without problems, right? And then I could remove those
partitions, so on and so forth. At least that's what I've been doing for a while. But this is the first time, I've been "shrinking" partitions.

---

### Post by ajgreeny on 2012-06-04
> **gmoore777 said:**
> In regards to ajgreeny, technically, it makes sense to me that gparted
could make changes to partitions as members of an extended partition.
Lets say one still had 100 GB of unallocated space inside an extended 
partition. GParted is the tool that one would use to say, create 4 more
25 GB partitions. Without problems, right? And then I could remove those
partitions, so on and so forth. At least that's what I've been doing for a while. But this is the first time, I've been "shrinking" partitions.
You are misunderstanding my point, I think.

If all the partitions you were working on were logical partitions within the sda3 extended partition, which is how things appear to be, then the extended partition was mounted, or more correctly, it was active when you worked on both sda5 and sda8, so as I understand gparted's way of working, it should have been impossible to do what you are saying you did, and maybe that is the cause of your problem.

---

### Post by gmoore777 on 2012-06-04
Well, my /dev/sda5 is now bootable.
Replying from that booted partition as we speak.

This is what I did.

I booted up a PrecisePangolin LiveCD, and ran various commands
but I think these last 2 did something constructful.

    sudo mke2fs -n /dev/sda5

That gave me a list of all the addresses of where the backups that were
made of the superblock.
I didn't think this is useful as I my superblock isn't corrupt with 
gibberish, it just
has the old entry in it on the size of the filesystem.

But to amuse myself, I then ran this command using "32768" as one of
those addresses returned from `mke2fs`:

    sudo e2fsck -b 32768 /dev/sda5

It complained of something, and I thought I hit "n" to answer no to 
something to get out of that command.
But then when I went back to that window to paste another command in it,
that `e2fsck` was still waiting for a response, and i think I hit
the carriage return, and it went further along fixing inodes and such.
(I couldn't scroll up enough to actually see how this all started).
Then I started hitting "n" to answer no and get out of it.

Then when I ran this command, it didn't fail like it used to:

ubuntu@ubuntu:~$ sudo resize2fs -f /dev/sda5

resize2fs 1.42 (29-Nov-2011)
The filesystem is already 2560142 blocks long.  Nothing to do!

ubuntu@ubuntu:~$

This was what I was trying to do, get the superblock to think
the filesystem is 2560142 blocks long, and not the old value it had of 
3586958.

In summary, not sure why GParted put it in this mess, and I'm not
entirely sure how I just fixed this.

Now to resize my /dev/sda8 partition and grab that free 4 GB space.
I feel confident that I will end up with another mess.

---

### Post by gmoore777 on 2012-06-04
Resizing my /dev/sda8 partition and grabbing the free 4 GB space
preceding it, just worked successfully.
I didn't think that grub stage 1 or 2 would be found 
on reboot since
the space would be added to the front of the partition
thus messing up any of the /boot and grub stuff.

But the "moving to the left" message that GParted puts up,
must move everything up to the beginning.

---

