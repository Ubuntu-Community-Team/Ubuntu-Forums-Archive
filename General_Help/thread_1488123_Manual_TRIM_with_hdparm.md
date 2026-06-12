---
title: "Manual TRIM with hdparm"
date: 2010-05-19
forum: General Help
---

### Post by 98cwitr on 2010-05-19
Just got my SSD, I'd like to write a bash script to run manual trim using hdparm. I've search and haven't found anything specific. Can someone provide some code plz? Thanks.

---

### Post by fjf on 2010-05-20
[http://www.ocztechnologyforum.com/forum/showthread.php?60882-wiper.sh-discussion-thread-%28Linux-TRIM-tool%29](http://www.ocztechnologyforum.com/forum/showthread.php?60882-wiper.sh-discussion-thread-%28Linux-TRIM-tool%29)

---

### Post by 98cwitr on 2010-05-20
are you just suggesting to use the wiper.sh script? b/c I really don't see whatever it was you were referring to :?

---

### Post by ariel on 2010-05-20
> **98cwitr said:**
> Just got my SSD, I'd like to write a bash script to run manual trim using hdparm. I've search and haven't found anything specific. Can someone provide some code plz? Thanks.

did you find this? it appears you also need to update hdparm, the one in lucid does not support TRIM - AFAIK

---

### Post by 98cwitr on 2010-05-21
> **ariel said:**
> did you find this? it appears you also need to update hdparm, the one in lucid does not support TRIM - AFAIK

fuuuuuuuuuu

Ill try that when I get home.

---

### Post by 98cwitr on 2010-05-22
woohoo....got it.

> 
brett@brett-desktop:~/hdparm-9.28/wiper$ sudo bash wiper.sh /dev/sda1

wiper.sh: Linux SATA SSD TRIM utility, version 2.6, by Mark Lord.
Preparing for online TRIM of free space on /dev/sda1 (ext4 mounted read-write at /).
This will be a DRY-RUN only.  Use --commit to do it for real.
Creating temporary file (41940000 KB).. 
Syncing disks.. 
Simulating TRIM operations..
(dry-run) trimming 83880000 sectors from 1401 ranges
Removing temporary file..
Syncing disks.. 
Done.
brett@brett-desktop:~/hdparm-9.28/wiper$ 


---

### Post by ariel on 2010-05-24
> **98cwitr said:**
> woohoo....got it.


It would really help if you post the steps you had to follow to get it to work. Also wondering if it really works (you need to use the --commit option to do the real TRIMming).
Thanks

---

### Post by 98cwitr on 2010-05-24
oh my bad...I did in another thread...it sure would be nice if a mod would merge them :)

[http://ubuntuforums.org/showthread.php?t=1490602](http://ubuntuforums.org/showthread.php?t=1490602)

---

### Post by Elfy on 2010-05-24
Closed - see the thread 98cwitr refers to.

---

