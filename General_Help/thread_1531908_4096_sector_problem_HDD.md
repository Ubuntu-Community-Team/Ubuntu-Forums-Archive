---
title: "4096 sector problem HDD"
date: 2010-07-15
forum: General Help
---

### Post by extasy on 2010-07-15
Hi, I've been searching the net for help but I can't find it. I'm a Ubuntu 9.10 user and have baught a WD 1.5TB HDD. When just formating it with gparted it's extreemly slow!

I have read that with gparted 0.51 there are ways to get this harddrive to work correct but there are no 0.51 packages available for 9.10.

Anyone who can help me with this problem?

kind regards
Henrik.

---

### Post by jpl888 on 2010-07-15
Yes I can help you. If you are using an older partitioning program it has probably defaulted to the older partitioning defaults which start at sector 63 and are completely incorrect for the newer large hard drives and SSDs. Hence the slowness.

Post back the results of```
sudo fdisk -l /dev/sda
```

to confirm.

---

### Post by Skaperen on 2010-07-15
I preformatted using fdisk running from a live CD.  Every partition was placed on an exact multiple of 2048 sector boundary.  You can do that at just every 8 sectors, but for other reasons, 2048 is even better (counted as 512 byte sectors for partitioning purposes).  It's exactly 1MB.  Then go re-run the install CD and manually assign the partitions when you get to that point.

---

### Post by jpl888 on 2010-07-15
Yes concurring with Skaperen if you partition a drive at the 1Mb boundary it covers all eventualities for sector size since it is divisible by all possible sizes up to 1Mb.

---

### Post by extasy on 2010-07-16
> **Skaperen said:**
> I preformatted using fdisk running from a live CD.  Every partition was placed on an exact multiple of 2048 sector boundary.  You can do that at just every 8 sectors, but for other reasons, 2048 is even better (counted as 512 byte sectors for partitioning purposes).  It's exactly 1MB.  Then go re-run the install CD and manually assign the partitions when you get to that point.


Thank you for your answer, but is there a how to for counting the size of the hdd and then the next steps?
Should I use sudo fdisk -l /dev/sda, do I need to manually enter start sector?

Kind regards
Henrik

---

### Post by dino99 on 2010-07-16
here is my favourite prog: [http://partedmagic.com/](http://partedmagic.com/)

boot on it to prepare your devices

---

### Post by extasy on 2010-07-16
> **dino99 said:**
> here is my favourite prog: [http://partedmagic.com/](http://partedmagic.com/)

boot on it to prepare your devices

Will this application help me with it all? Does this application detect the 4k sector and then set it up accordantly?

---

### Post by cascade9 on 2010-07-16
As far as I know, parted magic currently wont align the sectors on a WD 4k drive yet. 

Hmm...I dont have my links to the 'how to setup a WD advanced format' drive heere, I'll have to edit that in later...

---

### Post by extasy on 2010-07-16
> **cascade9 said:**
> As far as I know, parted magic currently wont align the sectors on a WD 4k drive yet. 

Hmm...I dont have my links to the 'how to setup a WD advanced format' drive heere, I'll have to edit that in later...

Thanks looking forward to it!

---

### Post by jpl888 on 2010-07-16
If you look at [http://wiki.ubuntuforums.org/showthread.php?t=1383771&page=9](http://wiki.ubuntuforums.org/showthread.php?t=1383771&page=9)

Jarige gives a comprehensive how to based on information I gave.

---

### Post by extasy on 2010-07-16
> **jpl888 said:**
> If you look at [http://wiki.ubuntuforums.org/showthread.php?t=1383771&page=9](http://wiki.ubuntuforums.org/showthread.php?t=1383771&page=9)

Jarige gives a comprehensive how to based on information I gave.

Thanks that wiki solved my problem! Now I got the HDD working. however I have called WD and told my mind to the responsible for my WD country office.

---

### Post by jpl888 on 2010-07-16
> **extasy said:**
> Thanks that wiki solved my problem! Now I got the HDD working. however I have called WD and told my mind to the responsible for my WD country office.

Que?

I don't know why you rang WD. It isn't a problem with the hard drive it's the operating system. Lucid's fdisk uses the 1MB boundary by default when you choose c and u as it recommends on start up.

---

