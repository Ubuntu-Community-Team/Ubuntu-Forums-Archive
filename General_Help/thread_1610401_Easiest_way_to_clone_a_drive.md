---
title: "Easiest way to clone a drive?"
date: 2010-10-31
forum: General Help
---

### Post by rmcellig on 2010-10-31
I just came across this page that describes an easy way to clone a drive. Is there an easier way than this (other options). What I like about this solution is that I just have to paste in the line of code and the machine is cloned. Can I clone back to the original drive if the original drive for whatever reasons goes south? If I clone back, will it be bootable?

My friend has just decided to switch from Mac to Ubuntu so being a newbie, she has a lot of questions. I am looking for the easiest way for her to clone her main drive.

[http://tinyurl.com/2ed6wje](http://tinyurl.com/2ed6wje)

---

### Post by gzarkadas on 2010-11-08
Yes, you can clone back and the original will be bootable (since everything is copied, including the boot sector). 

In case the clone is a larger disk than the original, you will have to tell dd to copy only the blocks that the original has (with the `count=BLOCKS' option) when copying back; use fdisk -l to get the number of blocks of the original disk. 

You can also clone to a file in another hard disk; this is handy for cloning many small drives to a large one (for taking for example backups or snapshots).

---

### Post by dcstar on 2010-11-09
> **rmcellig said:**
> I just came across this page that describes an easy way to clone a drive. Is there an easier way than this (other options). What I like about this solution is that I just have to paste in the line of code and the machine is cloned. Can I clone back to the original drive if the original drive for whatever reasons goes south? If I clone back, will it be bootable?

My friend has just decided to switch from Mac to Ubuntu so being a newbie, she has a lot of questions. I am looking for the easiest way for her to clone her main drive.

[http://tinyurl.com/2ed6wje](http://tinyurl.com/2ed6wje)

Use **ddrescue** if you want to see progress of the job and/or the source drive has any bad blocks.

---

### Post by HermanAB on 2010-11-09
The easiest way to clone a drive is with cat or dd:
# cat /dev/sdX > /dev/sdY
# dd if=/dev/sdX of=/dev/sdY

Quite trivial really, but if you get the device names the wrong way around, then the result will be very disappointing.  Check the device names with dmesg and df or mount.

---

### Post by rmcellig on 2010-11-09
What is the difference between cat and dd?

---

