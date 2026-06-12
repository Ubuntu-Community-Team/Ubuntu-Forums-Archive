---
title: "root partition without free space"
date: 2009-12-30
forum: General Help
---

### Post by eskimo on 2009-12-30
Hi to all! i've a ubuntu hardy heron on my laptop with a big problem, because my root partition of 6.5Gb has only 28Mb of free space! so the system has problem when he has to use free space in /tmp directory...and i think i'll have problem with futures upgrades. How can i free some space or find a solution? i've already done cleaning procedures like apt-get clean, autoclean, autoremove, dpkg --purge unused conf and i've emptied the tmp dir. 
i don't know how to solve this...and i really don't understand why that partition grew so much...
thanks, Paolo

---

### Post by great_googley_moogley on 2009-12-30
6.5 GB is going to be a pretty tight fit. A fresh install is about 3 GB. As you add applications and accumulate data, you're going to run out pretty fast.   

I would recommend using the Disk Usage Analyzer (Applications -> Accessories -> Disk Usage Analyzer) to scan your drive and track down whatever's eating so much space. 

If you have lots of ram, you may be able to do away with your swap partition. I wouldn't recommend this if you have anything less than 1GB of ram, and even then things might get a little hairy.

---

### Post by plucky on 2009-12-30
> **eskimo said:**
> Hi to all! i've a ubuntu hardy heron on my laptop with a big problem, because my root partition of 6.5Gb has only 28Mb of free space! so the system has problem when he has to use free space in /tmp directory...and i think i'll have problem with futures upgrades. How can i free some space or find a solution? i've already done cleaning procedures like apt-get clean, autoclean, autoremove, dpkg --purge unused conf and i've emptied the tmp dir. 
i don't know how to solve this...and i really don't understand why that partition grew so much...
thanks, Paolo

Checkout this [link](http://ubuntuforums.org/showthread.php?t=898573&highlight=drs305)

Do you have a separate /home partition?
Possibly a log file growing too large.
A backup not going to the correct location.

Post output from a terminal of ```
df -hT
```

Good Luck

---

### Post by eskimo on 2010-01-03
thanks, my trashes are ok and i've a separate partition for /home. Searching for big files wasn't useful.
I really don't know how to solve without taking space from swap partition, because i've 4Gb of ram

---

### Post by audiomick on 2010-01-03
I had to sort out this problem for a friend recently. I just took a few GB from /home and added it to /

Is there any reason you can't do this?

---

### Post by eskimo on 2010-01-05
I can do it, but i'd prefer to understand because my hardy root partition's content has doubled in size! i can't undestand because it's 6.5 Gb instead of 3-4Gb!! i've added some programs but not many!

---

### Post by philinux on 2010-01-05
> **eskimo said:**
> I can do it, but i'd prefer to understand because my hardy root partition's content has doubled in size! i can't undestand because it's 6.5 Gb instead of 3-4Gb!! i've added some programs but not many!

Uninstall any old kernels. I usually keep 2. Also check in /var/log.

The disk usage analyser will help you with this.

---

