---
title: "damaged file system"
date: 2012-06-10
forum: General Help
---

### Post by traditionalist on 2012-06-10
I have three corrupt blocks in my file system. This is causing various problems. I could reinstall but I would like to try and repair the faults.

How do I get fsck to carry out a repair on my root system from a live cd?

---

### Post by Tombradyhasamachinehead on 2012-06-11
hi,
You need to give us more information. What filesystem are you using first?

if you using ext4, you can open the terminal in a live cd and do

sudo e2fsck -f /dev/XXX

but please do it when the filesystem is unmounted!

where XXX is the drive like if i want to run fsck on my home parition i would do

sudo e2fsck -f /dev/sda3

---

### Post by carl4926 on 2012-06-11
You can use gparted too

---

### Post by Tombradyhasamachinehead on 2012-06-11
> **carl4926 said:**
> You can use gparted too

Yes that would probably be easier than the command line

---

### Post by traditionalist on 2012-06-11
Thanks a lot. System is ext4.  Gparted does not fix the problem.  When using clonezilla to run an image it finds and repairs the three blocks while copying the image.  I suppose I could just move the repaired image back to the drive, but I thought it must be possible to do it using fsck.  Will try that now and see what happens. Thanks again!

---

### Post by traditionalist on 2012-06-11
That gives;

```
mike@mike:~$ sudo e2fsck -f /dev/sdc1
[sudo] password for mike: 
e2fsck 1.42 (29-Nov-2011)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sdc1: 209312/3670016 files (0.2% non-contiguous), 2608135/14653440 blocks
mike@mike:~$ ^C
mike@mike:~$ 

```So I assume everything is OK again. Not sure about the 0.2% non-contiguous.  Will see if the errors have now stopped when using certain procedures.

---

