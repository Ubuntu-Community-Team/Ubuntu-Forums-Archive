---
title: "Is it possible to convert my external drives from fat32 to ext3 without loss of data?"
date: 2011-02-25
forum: General Help
---

### Post by mistergoomba on 2011-02-25
I have 2 external drives that I'm using for movies and they're both formatted to fat32. The problem I'm experiencing now is that some of the high quality mkv files are not able to be moved to the drive because of fat32's limitations.

I'd like to convert to ext3 (or 4) and I wanted to check to see if I can do it without having to reformat and without loss of data.

Thanks

---

### Post by kvizzel on 2011-02-25
sorry, not possible.

---

### Post by seawolf167 on 2011-02-25
I *suppose *you could resize the current partition, format the unallocated space ext3, transfer data over, then repeat until you are finished... but that is definitely not something I'd suggest doing.

Basically, the real solution is to store the data somewhere else temporarily, reformat, the transfer then data back.

---

### Post by highspider on 2011-02-25
seawolf167 is right.   

sudo apt-get install gparted

system->administrator->gparted

ok if your drive is say 50g with 10g of used fat32 space then resize the drive to 

10g of fat32 and make new ext3 or ext4 partition of 40g
(this will take a long time)
(warning of possible data loss) I've never had data loss but there is a warning.
 
move all your data from the the 10g fat32 partition to the 40g ext3 partition.

now resize the ext3 drive to the full size of drive.

DON'T DO THIS UNLESS YOU UNDERSTAND HOW IT WORKS.

---

### Post by mistergoomba on 2011-02-25
Okay, well that's too bad. I read something about fat32 being converted in Windows to NTFS without data loss and got my hopes up that ext4 may behave the same.

Thanks for the info and the ideas for workarounds! I'm going to give the partition thing a try (very carefully)

---

