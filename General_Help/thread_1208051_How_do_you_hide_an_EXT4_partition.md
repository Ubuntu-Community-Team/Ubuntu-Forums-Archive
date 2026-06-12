---
title: "How do you hide an EXT4 partition?"
date: 2009-07-08
forum: General Help
---

### Post by brandon88tube on 2009-07-08
How do you hide an EXT4 partition from Windows XP? Windows gives me problems when it sees a partition it labels as "unknown" and just causes trouble. I wanted to hide my Linux partition as to avoid this, but I hit a "road block" so to speak. Windows doesn't give me the option under Disk Management to Change Drive Letter and Paths, which is the only way I know of hiding a partition. If I could get some help on this I would greatly appreciate it. Otherwise I can expect a lot of problems and the system failing to boot.

---

### Post by brandon88tube on 2009-07-09
Bump.

---

### Post by brandon88tube on 2009-07-10
Super BUMP!

---

### Post by unutbu on 2009-07-10
brandon88tube, please post 
```

sudo fdisk -l
```

---

### Post by Chronon on 2009-07-10
Very strange.  My XP installation is completely ignorant of my ext3 partitions.  It only displays the NTFS partitions.  Unfortunately, since this has been the default behavior since I installed Kubuntu around 8.04, I don't have any idea about what determines this behavior in Windows.

---

### Post by unutbu on 2009-07-10
I agree with you, Chronon -- I haven't heard of any other cases where Windows behaved badly due to the presence of ext4 partitions.

Just for the fun of imposing our will on computers, however,
I think you can hide partitions from Windows by changing the partition type to one of the "hidden partition types", like 17 (Hidden HPFS/NTFS). (At least that's my belief -- I don't have any Windows machines on which to test this.)

Linux does not care what partition type you set, so an ext4 filesystem can live happily inside a partition with partition type 17.

---

### Post by brandon88tube on 2009-07-11
> **unutbu said:**
> I agree with you, Chronon -- I haven't heard of any other cases where Windows behaved badly due to the presence of ext4 partitions.

Just for the fun of imposing our will on computers, however,
I think you can hide partitions from Windows by changing the partition type to one of the "hidden partition types", like 17 (Hidden HPFS/NTFS). (At least that's my belief -- I don't have any Windows machines on which to test this.)

Linux does not care what partition type you set, so an ext4 filesystem can live happily inside a partition with partition type 17.

Here is my fdsisk -l output
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5582e76e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223        7833    20972857+   5  Extended
/dev/sda3            7834       19457    93369780    7  HPFS/NTFS
/dev/sda5            5223        7833    20972826   83  Linux

```

I have no idea why its setup like this. I only should have 3 partitions, 2 NTFS and 1 EXT4. I'm also suprised its set at sda5 instead of 4

---

### Post by unutbu on 2009-07-11
Run
```

sudo sfdisk --change-id /dev/sda 5 17
```

This will change the partition type on sda5 from type 83 (Linux) --> type 17 (Hidden HPFS/NTFS).

You can check that it worked by running "sudo fdisk -l" again. You should see 
```

/dev/sda5            5223        7833    20972826   17  Hidden HPFS/NTFS  
```

Then boot into Windows and see if sda5 is hidden. If it doesn't work, the change is easy to revert. Just boot back into Ubuntu and run
```

sudo sfdisk --change-id /dev/sda 5 83
```

Let us know how it goes.

PS. sda5 is a logical partition inside sda2. Logical partitions always have device numbers >=5.

---

### Post by brandon88tube on 2009-07-11
I have no idea why its a logical partition though. I thought I selected primary...

---

### Post by brandon88tube on 2009-07-11
Umm, that didn't work... Grub couldn't find the drive because it was hidden. I had to boot using a LiveCD and change it back.

---

### Post by unutbu on 2009-07-11
Hm. I see. Sorry about that. :redface:

I don't know the solution then. :-k

---

### Post by brandon88tube on 2009-07-12
Just to let you know, I tried it again, but this time on a blank EXT4 partition and even though Linux sees it as being hidden Windows still sees the partition and can't determine what the file system type is.

---

