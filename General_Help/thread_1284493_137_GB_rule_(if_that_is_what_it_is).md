---
title: "137 GB rule (if that is what it is)"
date: 2009-10-06
forum: General Help
---

### Post by texas.chef94 on 2009-10-06
1. I upgraded the HD from 40 GB to 160 GB, but more importantly beyond beyond the end of BIOS if that indeed correct terminology.
2. Only learned this as result of error 18.
3. Upgraded BIOS correctly via ftp from HP
4. Partitioned attempting to use major portion said HD with XP primary, (2) ext3 partitions and a swap with a vision of reinstalling ubuntu which I did giving me a successful dual boot 9.04 and XP home.
5. Then attempted load Lenny and received error 18
Note: Since then have tried several options and I used the subject title merely to ask what probably is a dumb question but here goes
Suppose I created a ntfs with 80 GB (thats half the HD. Then took up the rest in (2) ext3 partitions with a 2 GB swap  (I have 1 GB RAM)
Under these circumstances (rather unconventional) could I not load 2 Linux OS with no fear of error 18 as I would be well within the 137 GB range.

Please advise

---

### Post by Milos_SD on 2009-10-06
I am not sure, but I think that you can get rid of that error just by creating /boot partition.

---

### Post by oldos2er on 2009-10-06
What are the computer's specs?

---

### Post by texas.chef94 on 2009-10-06
> **oldos2er said:**
> What are the computer's specs?

Presario 2590US
System Specs
Type of system: 	Laptops
Bus Architecture: 	USB/PCMCIA
Hard Drive Bus: 	EIDE
Native OS: 	Windows XP Home
CPU Type: 	2.3GHz Intel Mobile Pentium 4
Memory Specs
upgraded from 40 GB HD to 160 GB
Memory Expansion: 	2 sockets
Memory Comments: 	PC2100 DDR SDRAM SODIMMs
p/nDM761A#ABA
C/N CNF34303TZ
processor intel (R) pentium (R)4
speed 2300 MHz
1 GB RAM
p/n CNF 34303TZ
As stated I upgraded BIOS to fit the increased HD at HP direction

---

### Post by texas.chef94 on 2009-10-06
> **oldos2er said:**
> What are the computer's specs?

The error messages do not concern me as much as establishing a partition arrangement that utilizes majority of the HD

Thanks

---

### Post by dcstar on 2009-10-06
> **texas.chef94 said:**
> 
........
Suppose **I created a ntfs with 80 GB** (thats half the HD. Then took up the rest in (2) ext3 partitions with a 2 GB swap  (I have 1 GB RAM)
Under these circumstances (rather unconventional) could I not load 2 Linux OS with no fear of error 18 as I would be well within the 137 GB range.

Please advise

If you have an issue where the boot loader is required to be at the front part of the drive, simply create/move your biggest partition to the end of the drive - then it will be installed in a vacant area at the start of the drive.

---

### Post by oldos2er on 2009-10-06
You could create a 1GB /boot partition at the beginning of the drive.

---

### Post by oldfred on 2009-10-07
I agree with oldos2er and Milos_SD on a separate /boot or you can go to have just grub in a small partition at the beginning of the hard drive. 

Herman on grub only partition:
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

---

