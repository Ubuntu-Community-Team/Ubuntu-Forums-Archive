---
title: "Increase partition size"
date: 2011-08-06
forum: General Help
---

### Post by Sef on 2011-08-06
How does one back up the oses and increase the partition size?

I have a dual boot of Windows 7 and Ubuntu and have made the partitions for each too small. I want to save them and then reinstall them on the new partitions. I've tried clonezilla, but it only restores them to the original partitions. How can I reinstall them on the new partitions?

---

### Post by dandnsmith on 2011-08-06
In general terms, I'd boot from a LiveCD (either Linux or Gparted CD), and use gparted to get stuff moved and resized.
For Windows7 I'd ensure the space was available and then grow the partition from Win7, if possible. I'd also be wary about moving the low-address end of Win7, in case it messes up booting of Win7 (as I've little idea, and no practical experience of doing this).

---

### Post by Sef on 2011-08-06
> In general terms, I'd boot from a LiveCD (either Linux or Gparted CD), and use gparted to get stuff moved and resized.


GParted can increase the size of the partition, but it cannot move an os from one partition to another.

---

### Post by Furball588 on 2011-08-06
Normally, I might think that doing something like dd if=/dev/sda1 of=/dev/sdb1 would do what you're asking, but for some reason I'm thinking you're looking for a little more then just that...

---

### Post by haqking on 2011-08-06
> **Sef said:**
> How does one back up the oses and increase the partition size?

I have a dual boot of Windows 7 and Ubuntu and have made the partitions for each too small. I want to save them and then reinstall them on the new partitions. I've tried clonezilla, but it only restores them to the original partitions. How can I reinstall them on the new partitions?

what do you mean Clonezilla will only restore to original partitions ?

the limitation is equal or larger for the destination ?

I am confused as to why clonezilla wont let you do it, it seems a perfectly normal situation

---

### Post by dandnsmith on 2011-08-07
After reading the thread, completely, I wonder if we have the whole picture.
Are the 'new' partitions on the existing HDD or another?
Do you really want to have to reinstall?

If the partitions are really different in size and position, then ignore my original suggestion (in which I thought the problem was merely to reshuffle space and assign more to the partitions holding the OSs), and think about using partimage - which I find far more versatile, and with which I am intending to transport a configured Ubuntu to a foreign location which doesn't have the luxury of a broadband connection (my experiments so far suggest this will work).

---

### Post by niko123456 on 2011-08-07
i've always found it amazing that you can resize an NTFS partition without formatting it, but you can't do the same to an ext partition.

although I wish I could be proved wrong.

---

### Post by haqking on 2011-08-07
> **niko123456 said:**
> i've always found it amazing that you can resize an NTFS partition without formatting it, but you can't do the same to an ext partition.

although I wish I could be proved wrong.


since when ?

Gparted and other tools resize ext with no problems ?

[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)

---

### Post by niko123456 on 2011-08-07
> **haqking said:**
> since when ?

Gparted and other tools resize ext with no problems ?

[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)

without formatting it? ie, I can shrink my ext4 partition??

---

### Post by haqking on 2011-08-07
> **niko123456 said:**
> without formatting it? ie, I can shrink my ext4 partition??


are you reading the features link i provided ;-)

there are other tools too like resize2fs

---

### Post by niko123456 on 2011-08-07
> **haqking said:**
> are you reading the features link i provided ;-)

I am now.. I'm just dubious...

---

### Post by haqking on 2011-08-07
> **niko123456 said:**
> I am now.. I'm just dubious...


you are dubious because the site shows you the feature, and i told you it does ?

okay ;-)

why dont you try it, it takes a few mins depending on the size you want to change

---

### Post by haqking on 2011-08-07
simple

---

### Post by niko123456 on 2011-08-07
> **haqking said:**
> you are dubious because the site shows you the feature, and i told you it does ?

okay ;-)

why dont you try it, it takes a few mins depending on the size you want to change

dubious because I swear I could never do this the last time I tried (admittedly at least a year ago). and dubious because the features don't say anything about without having to format/wipe the drive. i want to reclaim some free space and use it for another partition. 

i'm still dubious! haha.

---

