---
title: "deleted partition on portable hard drive"
date: 2010-01-28
forum: General Help
---

### Post by glenuk on 2010-01-28
i was reformatting the hard drive of a laptop & in doing so i accedently deleted the partition of the portable hard drive & now the hard drive dosent show up is there a way to fix this & get the data back
thanks 
glen

---

### Post by gabo.cr on 2010-01-28
Do you mean the MBR partition?
Can you see the HD using a live CD ?

---

### Post by glenuk on 2010-01-28
the whole partition has gone it doesnt even show up in windows
glen

---

### Post by mk1w86 on 2010-01-28
Could you please post the output of:

> sudo fdisk -l

so we can see if there are any remaining partitions on the drive.

To recover partitions you might want to take a look at TestDisk:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by glenuk on 2010-01-28
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes 
255 heads, 63 sectors/track, 121601 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xb8abb8ab 


Device Boot Start End Blocks Id System 
/dev/sda1 * 1 13 102400 7 HPFS/NTFS 
Partition 1 does not end on cylinder boundary. 
/dev/sda2 13 121602 976657408 7 HPFS/NTFS 
Partition 2 does not end on cylinder boundary. 


Disk /dev/sdb: 320.0 GB, 320072933376 bytes 
255 heads, 63 sectors/track, 38913 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x0d3c4912 


Device Boot Start End Blocks Id System

---

### Post by glenuk on 2010-01-28
i hope that the data can be recovered as there are some files there that arent mine & i need to put them back

---

### Post by audiomick on 2010-01-28
Your chances of recovering are at their best if you have not tried to write anything to the HD before you try and recover.
I would suggest unplugging it until you are ready to try testdisk, or whatever you decide to try.

I wont offer more advice than that, as I have never tried a recovery, only read stuff about doing it here.

---

### Post by glenuk on 2010-01-28
the hard drive powers on but i cant find anything about the drive anywhere on my comp or the laptop 
i'm in a right panic
glen

---

### Post by audiomick on 2010-01-28
Yes, the partition table is gone, so it wont show up.

According to your fdisk output, there is a 320GB partition with no partitions on it. I also don't see anything that could be a Linux install.
Did you shoot it down with your mistake?

Go and read this
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
for a start. It will at least give you an idea of where you stand.

And don't panic...

---

### Post by chewearn on 2010-01-28
The TestDisk app linked by mk1w86 in post #4 is the right tool for recovering a deleted partition.  I have used it before and it worked.  To install, click [here]("apt://testdisk") or type this command in terminal:
```
sudo apt-get install testdisk
```

Also, as pointed out by audiomick in post #7, do not write to the lost partition until you are ready to recover it.

---

### Post by glenuk on 2010-01-28
it was human error that got me into the situation but i have managed to get it sorted thank you all
glen

---

### Post by audiomick on 2010-01-28
good to hear.:p

---

