---
title: "Does LVM format when expanding?"
date: 2010-02-15
forum: General Help
---

### Post by Zilioum on 2010-02-15
I used to 500gb harddrives, formatet to ext4 to create a LVM. Today I added a 1TB disk which was previously formatet to ext3. I deleted the old partition on the disk, made a new one, set it to LVM and then added it to my VG "storage".
```
sudo vgextend storage /dev/sdb1
```
I then extended the LV "files" to use the whole VG.
```
sudo lvextend -l476934 /dev/storage/files
```
Now I have a have 1.8TB LV (the numbers add up), but I dont really know what happened with the ext3 of the 1TB disk. Did it get formated to ext4 when I expanded it? Should I have created a ext4 LV on the disk first before adding it to the "files" LV? 
What is also odd, is that when I log into my server it says "/media/mediadisk is using 98.7% of 916.90GB" (thats where I mounted the LV) altough when I use ```
sudo lvdisplay
``` it says that my LV is 1.8TB big.

Cheers

---

### Post by bluefrog on 2010-02-15
you need to resize2fs then

e2fsck -f /dev/storage/files
resize2fs /dev/storage/files

---

### Post by Zilioum on 2010-02-15
> **bluefrog said:**
> you need to resizefs then

resizefs what? And what will that do?

Cheers

---

### Post by falconindy on 2010-02-15
```
NAME
       resize2fs - ext2/ext3/ext4 file system resizer

SYNOPSIS
       resize2fs [ -fFpPM ] [ -d debug-flags ] [ -S RAID-stride ] device [ size ]

DESCRIPTION
       The  resize2fs  program  will resize ext2, ext3, or ext4 file systems.  It can be used to enlarge or shrink an unmounted
       file system located on device.  If the filesystem is mounted, it can be used to expand the size of the mounted  filesys&#8208;
       tem,  assuming  the kernel supports on-line resizing.  (As of this writing, the Linux 2.6 kernel supports on-line resize
       for filesystems mounted using ext3 only.).
```

The man page goes on to mention:
```
 If size parameter is not specified, it will default to the size of the partition.
```

---

### Post by Zilioum on 2010-02-15
> **falconindy said:**
> ```
NAME
       resize2fs - ext2/ext3/ext4 file system resizer

SYNOPSIS
       resize2fs [ -fFpPM ] [ -d debug-flags ] [ -S RAID-stride ] device [ size ]

DESCRIPTION
       The  resize2fs  program  will resize ext2, ext3, or ext4 file systems.  It can be used to enlarge or shrink an unmounted
       file system located on device.  If the filesystem is mounted, it can be used to expand the size of the mounted  filesys&#8208;
       tem,  assuming  the kernel supports on-line resizing.  (As of this writing, the Linux 2.6 kernel supports on-line resize
       for filesystems mounted using ext3 only.).
```

The man page goes on to mention:
```
 If size parameter is not specified, it will default to the size of the partition.
```

What do I have to resize? The problem is, that my LV is already as big as my VG. lvdisplay gives me this ```
  

  LV Name                /dev/storage/files
  VG Name                storage
  LV UUID                1Rcm52-GbF7-J1b0-H5Vb-3lQU-K8fm-FMBJP7
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                1.82 TB
  Current LE             476934
  Segments               3
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0

``` 

But I still get this ```
 => /media/mediadisk is using 98.7% of 916.90GB
```

---

### Post by speed32219 on 2010-02-15
Post output of this df -h

---

### Post by Zilioum on 2010-02-15
> **speed32219 said:**
> Post output of this df -h

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             146G  3.0G  135G   3% /
udev                  249M  244K  249M   1% /dev
none                  249M     0  249M   0% /dev/shm
none                  249M  300K  249M   1% /var/run
none                  249M     0  249M   0% /var/lock
none                  249M     0  249M   0% /lib/init/rw
/dev/mapper/storage-files
                      917G  905G     0 100% /media/mediadisk

```

---

### Post by Zilioum on 2010-02-15
One thing that I tried to do, is to remove the 1TB disc from the VG and try it again (with more reading in advance :p )

But I get this:
```
sudo vgreduce storage /dev/sdb1
  Physical volume "/dev/sdb1" still in use

```

I read that you have the PE to remove the disc, so now tried it with:```
 sudo pvmove -v /dev/sdb1
    Finding volume group "storage"
  No extents available for allocation

``` 

But this fails as well, since the disc is empty.
Any ideas?

---

### Post by Zilioum on 2010-02-15
> **bluefrog said:**
> you need to resize2fs then

e2fsck -f /dev/storage/files
resize2fs /dev/storage/files

I did that now, but still the same problem:
> But I get this:
Code:

sudo vgreduce storage /dev/sdb1
  Physical volume "/dev/sdb1" still in use

I read that you have the PE to remove the disc, so now tried it with:
Code:

 sudo pvmove -v /dev/sdb1
    Finding volume group "storage"
  No extents available for allocation

But this fails as well, since the disc is empty.
Any ideas? 

---

### Post by bodhi.zazen on 2010-02-15
You need to resize your partitions from a live CD. Resizing a LVM partition is performed manually, first you resize the LVM then you resize the file system.

See this link : 

[ResizeEncryptedPartitions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ResizeEncryptedPartitions#preview") 

It is for encrypted partitions, but this includes LVM as well, just skip the part about the crypt.

Otherwise see:

[http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html](http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html)

---

### Post by Zilioum on 2010-02-15
> **bodhi.zazen said:**
> You need to resize your partitions from a live CD. Resizing a LVM partition is performed manually, first you resize the LVM then you resize the file system.

See this link : 

[ResizeEncryptedPartitions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ResizeEncryptedPartitions#preview") 

It is for encrypted partitions, but this includes LVM as well, just skip the part about the crypt.

Otherwise see:

[http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html](http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html)

Doing this right now. But why do I have to resize it? By how much? And it says in the HowTo: > 1. Reduce the size of your file system with resize2fs (this tool works on ext2 and ext3 partitions) Will this be a problem, because my VG is ext4?

---

### Post by falconindy on 2010-02-15
You have to resize it because you only expanded the container that the filesystem resides in. Imagine you add a new wing onto your house. The wing is, of course, empty when it's built. You still need to furnish it.

There's no need to be concerned with specifics of how much to expand the filesystem by because resize2fs will take care of that for you by just specifying the device (as per the man page). Being Ext4 isn't a problem -- Ext filesystems are all functionally the same at a low level so that the same set of utility programs that works on Ext2 also works on Ext3 and Ext4.

---

### Post by Zilioum on 2010-02-15
I think it works now, thanks a lot for all your help!
With dh -f I get: ```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             146G  3.0G  135G   3% /
udev                  249M  252K  249M   1% /dev
none                  249M     0  249M   0% /dev/shm
none                  249M  304K  249M   1% /var/run
none                  249M     0  249M   0% /var/lock
none                  249M     0  249M   0% /lib/init/rw
/dev/mapper/storage-files
                      1.8T  905G  837G  52% /media/mediadisk

```

Some questions remain though: Why is does it say /dev/mapper/storage-files and not /dev/storage/files ?
What did initially do wrong? Did I forget to expand the lv? Is lv=filesystem? And how did I fix it exactly? Did my new disk get formatted automatically when I extended the lv? (asking because I thought it expanded very fast)

Thanks again for your help and patience.

---

### Post by bodhi.zazen on 2010-02-15
No offense intended, but I suggest you take the time to review any of the on line guides on LVM

[http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)

If you have a specific question, please ask, but asking us to re-type and explain LVM to you is a bit much, IMO.

---

### Post by Zilioum on 2010-02-15
NP, but I already read that, and I understand it. Sorry if I didnt put my question right, but what I didnt understand is in what state my file system was when the LV showed to be 1.8TB big but /media/mediadisk only 900gb (first post).
Second question: Why is does it say /dev/mapper/storage-files and not /dev/storage/files in my previous output of df -h?

---

### Post by bodhi.zazen on 2010-02-15
LVM takes physical disks (PV) and makes Logical Volumes (LV).


Physical partitions = /dev/sdxy

LV show up in /dev/mapper/name_of_Logical_Volume

---

### Post by Zilioum on 2010-02-15
Thanks a lot, my second question is answered. 
Still, why was the LV bigger than what was mounted in /media/mediadisk? Can it be that the 1TB disk was still mounted there and showed up on its own and in the LV? Or did I forgett to extend the VG and just made the LV bigger?(strange that this should be possible) Just trying to understand what happened.

---

### Post by bodhi.zazen on 2010-02-15
A physical partition is a container. It holds a file system. When you create and format a physical partition, the size of the file system == size of the container.

When you resize it with gparted, gparted first makes the physical partition, the physical container, larger, then expands the file system (contents) . It does this automatically and you do not see the step-by-step manual commands.

The LV is a container. It holds a file system. gparted does not work with LVM, so when you resize it you need to take each step manually. When enlarging you first use LVM to make the container (LV) larger (step 1) then in step 2 you expand the file system.

The physical partition or LV is a container, the file system is the contents, and the file system does not automatically resize itself simply because you make the container a different size.

Physical partition || LV != file system

Here is how to manually resize and ext3 file system on a physical partition :

[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

---

### Post by Zilioum on 2010-02-15
Now I get it, I made the mistake to assume that the file system grows with the LV. Thanks a lot for your help, I really appreciate the time and effort you put into this!

---

