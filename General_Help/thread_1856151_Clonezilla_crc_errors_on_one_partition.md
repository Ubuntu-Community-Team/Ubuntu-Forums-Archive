---
title: "Clonezilla crc errors on one partition"
date: 2011-10-07
forum: General Help
---

### Post by memilanuk on 2011-10-07
Hello all,

I picked up a 1.5TB portable HDD yesterday with the intent of backing up my 500GB HDD on my laptop.  The idea was to use clonezilla to create a backup image of the hdd, and then use Duplicity from within Ubuntu to regularly backup the users (mine) home directory, all to the portable drive.

Everything seems to be working for the most part... duplicity is backing up to a folder 'duplicity' on the portable drive, and clonezilla is able to create disk images of the partitions from the main laptop hard drive (sda) on the portable drive (sdb) in the directory 'clonezilla'.

The problem is that the laptop hdd has a number of partitions, the largest of which is sda1, a 385GB partition holding the original Windows Vista installation.  clonezilla goes thru the creation process just fine, but in the end when it goes back thru and performs error checking on all the partitions in the images it created, it coughs up a CRC error on the image of sda1.  Backing up a 500GB HD this way is slow, but I went thru and did a second error check run and it came up again, and then I did a complete second run creating new partition images, etc. and the error popped up again when running the checks.  Only on the image for sda1, not for any of the other partitions (sda5, sda6, sda7).

Any ideas what might be causing this, and how to manage it?

TIA,

Monte

---

### Post by memilanuk on 2011-10-11
BTT

Could really use some ideas on this one...

---

### Post by RZFeeser on 2012-03-06
Interesting. I'm having the same issue with Clonezilla. Clonezilla can image the partition fine, but I get a "CRC error again at 0..." error about 29% into checking the image.

I've attempted to run chkdisk on both the NTFS drive I am attempting to back up, and the ext3 destination drive; I have not discovered any errors.

Did you make any progress with your problem? Seeing as it did save correctly, I wonder if Clonzilla will still restore the image?

---

### Post by memilanuk on 2012-03-06
No progress here.  Ended up saving what info I could manually to an external backup drive, installed a new disk drive, and restored from the backup.

---

