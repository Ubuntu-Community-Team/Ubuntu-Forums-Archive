---
title: "windows destroyed my partitions"
date: 2011-07-25
forum: General Help
---

### Post by spezticle on 2011-07-25
in my computer i have two hdd's. A 500gb and an 80gb, both sata.
windows has the 80 all to itself and the 500 had a bunch of partitions that i use for ubuntu. for what its worth, i was using 11.04.

anyway, i had approximately 60gb of the 500 unallocated. while in windows i tried to create an ntfs partition from this 60gb space.

windows complained that there was an error, and that i should close the logical volume manager, reopen, and try again. I did and it complained the same.

I tried rebooting so i could use linux to do the job but was only booted to a grub rescue terminal.

i loaded a livecd of 11.04 to check out the partition table with gparted and it shows my entire 500gb hdd as unallocated now.

can somebody please help me so that i do not lose hundreds of gigs of data. this has happened just moments ago and i have not done anything to the drive contents, nor has any data been written since windows did whatever it did.

thanks in advance
:)

---

### Post by Quackers on 2011-07-25
Don't mess with Linux partitions from within Windows - it can't handle them. It has probably tried to encroach on a Linux partition.

testdisk should be able to restore your partitions. Have a look at the links below. The second one is the best Howto.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

---

### Post by spezticle on 2011-07-25
Thanks. I should have known not to even bother trying to create the partition while in windows. lesson learned. testdisk is doing its thing. we'll see what happens.

---

### Post by Quackers on 2011-07-25
Should be ok! Good luck :-)

---

### Post by spezticle on 2011-07-25
This is all that it found, which is not at all what i'm looking for...
the disk was entirely an logical partition with exended partitions inside. i'm looking for my /home which was at the end and about the last 300gb. Also, that fat32lba partition must be really old because i haven't had a fat32 partition in years. 
can i just guess at the size and then scan to find files or is that not an effective way to recreate the partition?


```
TestDisk 6.12, Data Recovery Utility, May 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition               Start        End    Size in sectors
>D Linux                    0  32 33  1958  64 26   31457280
 D Linux                  608   0  1  1130  42 32    8388608
 D FAT32 LBA            12176   1  1 36485 254 63  390540087
 D Linux                41360   0  1 42303 223 48   15163392
 D Linux                41377   1  1 42320 224 48   15163392
 D Linux                41385   1  1 42328 224 48   15163392

```
I forgot to mention, this is the result of a quick then deeper scan

---

### Post by spezticle on 2011-07-26
after doing the scan/deep scan a few times, i found the /home partition i was looking for. i wasn't able to rebuild the partition or the table, but i was able to access the drive well enough to copy the important contents to another disk and format/rebuild the hdd again. :)
thanks!

---

