---
title: "Disk Checking Issue After Partition Resize"
date: 2010-07-31
forum: General Help
---

### Post by Andysan on 2010-07-31
Hi all,

I have Win 7, Ubuntu Lucid and my laptop recovery partition setup as  a tri-boot using GRUB2, all pretty standard stuff.  I recently resized my Ubuntu partition in order to install Fedora for work.  Now when I boot Ubuntu I get a message prior to the GDM window that says:

```
Errors were found while checking the disk drive for /

```
Pressing 'F' to fix the errors then gives the following:

```
The disk drive for /tmp is not ready or not yet present

```
I can skip all of this and Ubuntu seems to still work fine but its annoying me - is there anyway I can fix it please?  My disk layout is as follows:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         784     6297448+  12  Compaq diagnostics
/dev/sda2   *         785       14234   108031516    7  HPFS/NTFS
/dev/sda3           14235       19457    41953747+   5  Extended
/dev/sda5           14235       17512    26329171+  83  Linux Ubuntu /
/dev/sda6           18023       19237     9759456   83  Linux Ubuntu Home
/dev/sda7           19238       19457     1767118+  82  Linux swap / Solaris
/dev/sda8           17512       17525      102400   83  Linux Fedora Boot
/dev/sda9           17525       18022     3992576   83  Linux Fedora / (and home on same partition)

Thanks!

---

### Post by ajgreeny on 2010-07-31
From the ubuntu Live CD run ```
sudo e2fsck -p /dev/sda5
``` which is your ubuntu / partition, and see if it goes through the check without a problem.  If it finds errors it should say what they are and then you can come back here for more info.  Very often this file-system check sorts out these sort of problems without any further action being needed.

See ```
man e2fsck
``` for more detailed info.

---

### Post by Andysan on 2010-07-31
Hi AJ,

Thanks, I just came across a post in [this ]("http://www.uluga.ubuntuforums.org/showthread.php?p=9437240")thread also by yourself detailing the same thing which I was about to try.

OK, I've run:

```
sudo e2fsck -p /dev/sda5
``` 

As instructed and the following is reported:

```
/dev/sda5: The filesystem size (according to the superblock) is 6582528 blocks 
The physical size of the device is 6582292 blocks
Either the superblock or the partition table is likely to be corrupt!

/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)

```

Just to confirm, this has come about as a result of resizing my partition to free up space for Fedora.  Thanks!

---

### Post by ajgreeny on 2010-07-31
OK, so now run ```
sudo e2fsck /dev/sda5
``` ie, without the -p option, as the error message suggests and see if it helps.

Incidentally, how did you shrink your partition to make the space?

---

### Post by Andysan on 2010-07-31
> **ajgreeny said:**
> OK, so now run ```
sudo e2fsck /dev/sda5
``` ie, without the -p option, as the error message suggests and see if it helps.

Incidentally, how did you shrink your partition to make the space?

OK, I'll give this a go in a sec and report back - didnt want to try it without checking with you in case I hosed something.

I just used the Fedora installer to shrink the Ubuntu / partition, then created the relevant Fedora partitions.

---

### Post by Andysan on 2010-07-31
> **Andysan said:**
> OK, I'll give this a go in a sec and report back - didnt want to try it without checking with you in case I hosed something.

I just used the Fedora installer to shrink the Ubuntu / partition, then created the relevant Fedora partitions.

Output is as follows:

```
sudo e2fsck /dev/sda5

e2fsck 1.41.11 (14-Mar-2010)
The filesystem size (according to the superblock) is 6582528 blocks
The physical size of the device is 6582292 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? yes
```

I dont seem to have the option to say @no@ to aborting.

---

### Post by ajgreeny on 2010-07-31
Well, this is all beyond me now, I'm afraid, and the only extra things I can suggest is that you firstly run ```
sudo fdisk -l
```from ubuntu and report the output back here.

It may also be worth a boot to the ubuntu live CD and use gparted to resize your ubuntu partition again, making sure that the option to round partitions to cylinders is checked and enabled.  Maybe the fedora partitioning utility does not work that way, I've never got on well with fedora so don't know, though generally these days this rounding should not make any difference.

---

### Post by Andysan on 2010-07-31
> **ajgreeny said:**
> Well, this is all beyond me now, I'm afraid, and the only extra things I can suggest is that you firstly run ```
sudo fdisk -l
```from ubuntu and report the output back here.

It may also be worth a boot to the ubuntu live CD and use gparted to resize your ubuntu partition again, making sure that the option to round partitions to cylinders is checked and enabled.  Maybe the fedora partitioning utility does not work that way, I've never got on well with fedora so don't know, though generally these days this rounding should not make any difference.

Hey AJ,

That was a really good idea to try and resize the partitions through GParted, unfortunately it uses e2fsck to make a check first and of course this fails.

Thanks for your help - I guess strangely the only annoying thing is that my system works fine, all distros running OK.  If I had hosed my Ubuntu install I'd just say what the heck and reinstall it.  Seeing as everything seems fine and I need to use this tomorrow I dont know if I can be bothered to reinstall everything - nothing is exactly "mission critical" anyway in terms of the data on there.

Thanks again for your efforts!

---

### Post by Andysan on 2010-07-31
I was about to give up but felt compelled to try the Live CD once more (actually, I lie - I was going to try [this]("http://pith.org/notes/2005/07/23/how-i-fixed-my-raid-1-partition-size-error/")).

Either way, I had one more go at a normal e2fsck and it ran - I guess before I could have accidentally hit Return one to many times but I swear it wasnt working.  Anyway, I still get the error on boot and now another message saying that there are serios issues with /.  Am going to try e2fsck -p now from the Live CD for kicks.

```

ubuntu@ubuntu:~$ sudo e2fsck /dev/sda5
e2fsck 1.41.11 (14-Mar-2010)
The filesystem size (according to the superblock) is 6582528 blocks
The physical size of the device is 6582292 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? no

/dev/sda5 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda5: 284805/1643376 files (1.1% non-contiguous), 1527907/6582528 blocks
ubuntu@ubuntu:~$ 

```


EDIT - OK, to anyone who may have a similar issue I bit my tongue and just went for it - after running e2fsck the solution was to run resize2fs to resize the filesystem and bring it inline with the partition:

```
resize2fs /dev/sda5
```

Thanks AJ for your help, if I ever meet you in a pub remind me that I owe you a pint sir!

---

