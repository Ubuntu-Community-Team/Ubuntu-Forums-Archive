---
title: "Installtion Help Partitioning"
date: 2010-05-26
forum: General Help
---

### Post by qwiktune on 2010-05-26
I have a dell here that has Windows XP installed on it [one 40g hard drive]. I'm at the Partitioning screen and im not sure which to select to have windows still on it but also Ubuntu so i can duel boot, also i'm using the alternative CD to install and when i go into Manual in the partitioning screen I see

#1 primary 41.1 MB fat16
#2 primary 36.2 GB ntfs
#3 primary 3.8GB fat32

i assume #2 is the windows xp partition, but what are the other 2 and how do I got about freeing up about 10gb for Ubuntu to duel boot? THANKS

---

### Post by spiky001 on 2010-05-26
Is this a laptop you are installing to & before you install you would be better off defrag windows 1st and backing up your data

---

### Post by qwiktune on 2010-05-26
Its a desktop and I just installed windows xp on it, installed drivers and firefox, theres nothing I need to backup

---

### Post by spiky001 on 2010-05-26
there should be an option to install along side windows, Is it the 2nd option?

---

### Post by qwiktune on 2010-05-26
Under Guided Partition? Theres

Guided - resize SCSI1 (0,0,0), partition #2 (sda- and use freed s
Guided - use entire disk
Guided - use entire disk and set up LVM
Guided - use entire disk and set up encrypted LVM
Manual

---

### Post by qwiktune on 2010-05-26
UNDER MANUAL listed is

Guided Paritioning
Configure software RAID
Configure the logical volume manager
Configure encrypted volumes

SCSI1 (0,0,0) (sda) - 40.0 GB ATA WDC WD400BB-75FJ
   #1 primary 41.1 MB fat16
   #2 primary 36.2 GB ntfs
   #3 primary 3.8GB fat32

Undo changes to partitions
Finish partitiong and write changes to disk

---

### Post by qwiktune on 2010-05-26
Do i go to Manual and pick the 3.8 fat32 partition and resize it or do I have to resize the 36.2 ntfs partition first...i not sure so i', just sitting on the screen until i know where to go about installing it lol

---

### Post by akakingess on 2010-05-26
Somebody please correct me if I am wrong, but is that 3.8 GB Partition the "Backup Partition" for Windows, in order of a problem it refers to that partition to get to the last known running configuration. You could do without it, if you do proper backups yourself either to DVD or some other way, but just wanted you to know what I believe that little partition is for.

---

### Post by spiky001 on 2010-05-26
Just trying to find out I do mine different I install win to 15gig on it,s own partition then when i install linux it gose on rest I think you wanna shrink windows give Ubuntu some room

---

### Post by qwiktune on 2010-05-26
So by doin that I can go into Manual, goto the 36.2 partition and change the size, then will a new partition appear that I can select to use for Ubuntu or whats the procedure, can I do it all here at this Partition disk screen?

---

### Post by spiky001 on 2010-05-26
Yes it should show windows at front of line then the rest should be spare

---

### Post by qwiktune on 2010-05-26
Well i resized the 32.2 partition and it made a new FREE SPACE one that saved as like 2 different partitions one is like #6 is 500mb swap and the other #7 is 10.2gb ext4 and fished partition and write to disk, so now I assume it is installing onto the ext4 partition?

---

