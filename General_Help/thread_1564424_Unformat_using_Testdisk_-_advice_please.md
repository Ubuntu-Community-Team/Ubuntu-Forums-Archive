---
title: "Unformat using Testdisk - advice please?"
date: 2010-08-30
forum: General Help
---

### Post by Martyn Thompson on 2010-08-30
Dear all,
You guessed it.  I have stupidly and inadvertently formatted my home partition on my other system while trying to 'downgrade' to Ubuntu 9.10.  I have isolated the hard drive and am currently using Testdisk to discover the partitions on there.  
The scan hasn't yet finished however it appears there are two entries of each partition.  Here:

Linux      0       1     1       4012   254  57    64468776
Linux      0       1     1       4012   254  57    64468776
Linux      4013    0     1       14032  254  59    160971296
Linux      4013    0     1       14032  254  59    160971296
Linux      9079    0     1       14032  254  61    79586008 [home]
Linux      9079    0     1       14032  254  61    79586008 [home]

When attempting the downgrade, I was wanting to keep the home folder (and root and swap) all at the same size.  I am pretty sure I fouled up by trying to revert the file system type to ext3 from ext4. 

Does anyone have any advice on which partition out of the two 'home' ones, I should be attempting to keep? I cannot see a difference between them but this is how testdisk has reported the drive.

Apart from the standard 'back up everything next time' and more fitting for me 'pack up your PC and never use it again!', does anyone have any specific advice on recovering my original home partition? 

Thanks,

Martyn.

---

### Post by Martyn Thompson on 2010-08-30
Further (finished) output from tesdisk...

Disk /dev/sdb - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
D Linux                    0   1  1  4012 254 63   64468782
D HPFS - NTFS              0   1  1 14592 254 63  234436482
D Linux                 4013   0  1 14032 254 63  160971300
D Linux                 9079   0  1 14032 254 63   79586010 [home]
D Linux Swap           14033   1  1 14592 254 63    8996337

---

