---
title: "USB drive not beign detected"
date: 2011-01-07
forum: General Help
---

### Post by Rodayo on 2011-01-07
I'm using a kingston data traveler. I've only used it on windows before.

The drive doesn't get detected automatically so I tried this command

mount /dev/sdb ./mnt_point

which gives me a message saying to specify the filesystem type

after some googling I found out it probably uses fat32(other types didn't work)

But if I try 

mount -t fat32 /dev/sdb ./mnt_point

it says it doesn't recognize that filesystem type. 

Anyone got a fix? I wish it were as simple as it is on windows

---

### Post by wilee-nilee on 2011-01-07
Does it show in computer?

Install gparted and look to see if it shows there and if the are any flags like a corrupted partition/files that might need a fix.

---

### Post by gmjs on 2011-01-07
Hi,

Just out of interest, is it the 'Secure Privacy Edition' of the Kingston Data Traveller?

The Secure Privacy Edition drive requires that a Windows executable is run that tells the device that the data partition on it (it has two partitions--one with the executable and one with the data) can be accessed.  This is done at the hardware level, thus making it very difficult to access without being able to run the executable.

I'll stop there just in case it's not the 'secure privacy' version but, if it is, I'm afriad you can't use it in any operating system other than Windows (and I don't use the one I was given at work on principle)!

Hope that helps.

Graham

---

### Post by wilee-nilee on 2011-01-07
> **gmjs said:**
> Hi,

Just out of interest, is it the 'Secure Privacy Edition' of the Kingston Data Traveller?

The Secure Privacy Edition drive requires that a Windows executable is run that tells the device that the data partition on it (it has two partitions--one with the executable and one with the data) can be accessed.  This is done at the hardware level, thus making it very difficult to access without being able to run the executable.

I'll stop there just in case it's not the 'secure privacy' version but, if it is, I'm afriad you can't use it in any operating system other than Windows (and I don't use the one I was given at work on principle)!

Hope that helps.

Graham

The thumb can't be wiped and reformatted to just being a plain thumb? Ah a encryption schema.

---

### Post by Rodayo on 2011-01-07
> **gmjs said:**
> Hi,

Just out of interest, is it the 'Secure Privacy Edition' of the Kingston Data Traveller?

The Secure Privacy Edition drive requires that a Windows executable is run that tells the device that the data partition on it (it has two partitions--one with the executable and one with the data) can be accessed.  This is done at the hardware level, thus making it very difficult to access without being able to run the executable.

I'll stop there just in case it's not the 'secure privacy' version but, if it is, I'm afriad you can't use it in any operating system other than Windows (and I don't use the one I was given at work on principle)!

Hope that helps.

Graham

thanks for trying but I was just being stupid =P

The drive was in /dev/sdb1 not /dev/sdb

I'm copying some files to the drive through the terminal right now.

---

### Post by gmjs on 2011-01-07
> **wilee-nilee said:**
> The thumb can't be wiped and reformatted to just being a plain thumb? Ah a encryption schema.

Ooops...should have spotted the lack of partition number--sorry!

Yes, the first partition cannot be erased--it mounts as a read-only CD.

---

### Post by dcstar on 2011-01-07
> **gmjs said:**
> Ooops...should have spotted the lack of partition number--sorry!

Yes, the first partition cannot be erased--it mounts as a read-only CD.

If you don't need that Windows rubbish just use **gparted** to write a new partition table to the drive (which will totally wipe it).

Then you can format the whole drive to how **you** want it.

---

