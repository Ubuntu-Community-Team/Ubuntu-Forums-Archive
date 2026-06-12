---
title: "mounting whole disk img"
date: 2010-09-16
forum: General Help
---

### Post by carlinuxlearner on 2010-09-16
This might be in the wrong forum. I don't know, I really had no idea where to put it, so please move it if necessary.

**What I did:**
Used ddrescue to clone a 500GB hard drive that was failing (read errors, wouldn't boot, etc...)
The command I used to do it was:
```
sudo ddrescue /dev/sdh /location/I/picked.img
```
Well it took it 2 days, but it finally got past all the errors and completed.

**What I'm trying to do:**
Now that I have a copy of it all, I want to mount the image and access the files.

**What's not working?**
When I enter:
```
sudo mount picked.img /where/I/want/to/mount/it/
```
it says: "mount: /location/I/picked.img is not a block device (maybe try `-o loop'?)"

And when I try ```
sudo mount -o loop picked.img /where/I/want/to/mount/it/
```
it says: "mount: you must specify the filesystem type"

Well the disk was partitioned with NTFS, so I try ```
sudo mount -t ntfs -o loop picked.img where/I/want/to/mount/it/
```

And the result is: 
> NTFS signature is missing.
Failed to mount '/dev/loop0': Invalid argument
The device '/dev/loop0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?



SOooo, what's wrong here? It seems to me I'm trying to mount it the wrong way, since it's an image of the whole disk, and not just one partition. And if that is the problem, then how do I mount it?

---

### Post by sisco311 on 2010-09-16
To mount a partition inside the disk image you need to calculate the offset of where the partition starts.

```
parted picked.img
```

```

GNU Parted 2.3
Using picked.img
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) **unit**                                                             
Unit?  [compact]? **B**                                                       
(parted) **print**
```

The output should look something like:
```
Model: ATA ST3160815AS (scsi)
Disk /dev/sda: 160041885696B
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start          End            Size           Type     File system     Flags
 1      **32256**B         10733990399B   10733958144B   primary  ext4
 2      **10733990400**B   21500881919B   10766891520B   primary  ext3
 3      **21500881920**B   158961761279B  137460879360B  primary  ext4
 4      **158961761280**B  160039272959B  1077511680B    primary  linux-swap(v1)

```

type **q** to exit from parted.

Now to mount a partition, you have to run something like:
```
sudo mount -o loop,offset=**32256** picked.img mount/point
```

---

### Post by carlinuxlearner on 2010-09-16
You, are a genius! :D

Not only did it solve my problem, but I learned something new while I was at it! It worked perfectly. Thank you!

---

### Post by sisco311 on 2010-09-16
You're welcome!

---

### Post by blueridgedog on 2010-09-16
> **sisco311 said:**
> To mount a partition inside the disk image you need to calculate the offset of where the partition starts.


Excellent and succinct help!

---

### Post by mips on 2010-09-18
> **carlinuxlearner said:**
> Well it took it 2 days, but it finally got past all the errors and completed.


In future rather try [safecopy]("https://sourceforge.net/projects/safecopy/"). I find it MUCH faster than ddrescue when it starts encountering bad sectors.

Here is a nice post on how to extract & mount partitions from image files [https://sourceforge.net/projects/safecopy/forums/forum/472935/topic/3495567](https://sourceforge.net/projects/safecopy/forums/forum/472935/topic/3495567)

---

### Post by dcstar on 2010-09-19
> **mips said:**
> In future rather try [safecopy]("https://sourceforge.net/projects/safecopy/"). I find it MUCH faster than ddrescue when it starts encountering bad sectors.


It is better to also tell people that the **safecopy** package is in the repositories. There is no need to download and manually install.

---

### Post by mips on 2010-09-19
> **dcstar said:**
> It is better to also tell people that the **safecopy** package is in the repositories. There is no need to download and manually install.

The link to sourceforge was for reference only.

---

