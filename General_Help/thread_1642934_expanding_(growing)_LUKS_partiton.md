---
title: "expanding (growing) LUKS partiton"
date: 2010-12-11
forum: General Help
---

### Post by BinaryMn on 2010-12-11
As a preface, I have spent three hours with Google, attempting various ideas with no luck. Please do not reply back telling me to search for the answer. I already have.

I have two machines. I'm upgrading the RAM in both and need to make a bigger swap space so suspend/hibernate doesn't break. Therein, lies my problem.

[--sda3--](-[--sda7--][--sda8--][--sda6--][--sda5--]-)[--sda2--]

I'm using a LVM inside a single LUKS partition(device?). Not the other way around (with LUKS on the LV, which is what everything I've read is assuming). In my scenario, sda7 is the partition with LUKS on it and inside are two LVs in a single VG. One is my root LV and the other is my swap. I'm trying to grow sda7 (sda8 is a 2GB empty partition that I want to grow sda7 over) so then I can resize the LVM and the swap LV.

the '# cryptsetup resize sda7_crypt' command doesn't do anything. I can't grow the swap LV because there isn't any space left on the PV. The PV is the LUKS partition and I can't get the LUKS partition to grow.

Please help.

---

### Post by BinaryMn on 2010-12-11
Bump.

---

### Post by bodhi.zazen on 2010-12-11
1. It is considered impolite to bump your threads in less then a day or so. We are a busy forums and we are all volunteers, so be patient.

2. See : [https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

---

### Post by BinaryMn on 2010-12-11
I made this thread late at night. I bumped it so it wouldn't be pages behind for anyone lurking during the day today.

---

### Post by BinaryMn on 2010-12-11
That walkthrough is incorrect. Not only did it not help, the partition with LUKS on it is no longer being recognized and for the moment, I've lost all my data.

Thanks.

---

### Post by bodhi.zazen on 2010-12-11
> **BinaryMn said:**
> That walkthrough is incorrect. Not only did it not help, the partition with LUKS on it is no longer being recognized and for the moment, I've lost all my data.

Thanks.

I am sorry you are having a problem. I guess you missed the big red warning at the top of the page re: backup first.

Hard lesson to learn, but if your data is important to you you need to back it up.

If you would like assistance, you will need to tell use what steps you have done and where you had a problem.

---

### Post by BinaryMn on 2010-12-11
> **bodhi.zazen said:**
> I am sorry you are having a problem. I guess you missed the big red warning at the top of the page re: backup first.

If you would like assistance, you will need to tell use what steps you have done and where you had a problem.

The backing up warning is a disclaimer. I don't have terabytes of storage to make backups. Please don't cite it unless you're going to give me the hardware to be able to make backups.

[http://ubuntuforums.org/showthread.php?t=1643334](http://ubuntuforums.org/showthread.php?t=1643334)

---

### Post by bodhi.zazen on 2010-12-11
> **BinaryMn said:**
> The backing up warning is a disclaimer. I don't have terabytes of storage to make backups. Please don't cite it unless you're going to give me the hardware to be able to make backups.

[http://ubuntuforums.org/showthread.php?t=1643334](http://ubuntuforums.org/showthread.php?t=1643334)

No it is not a "disclaimer". It is a warning and clearly states that data loss can occur.

> WARNING! Although unlikely (each step is reversible), resizing your encrypted partitions may result in data loss. BACKUP YOUR DATA FIRST

People who do not back up their data eventually loose it, no matter the size. I know because I see people learning and re-learning this lesson over and over.

It is not a matter of if hard drives will fail, it is a matter of when and what you have done to prep.

All hardware will eventually fail and when it does you will need a backup.

---

