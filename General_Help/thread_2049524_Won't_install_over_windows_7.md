---
title: "Won't install over windows 7"
date: 2012-08-28
forum: General Help
---

### Post by 711Savior on 2012-08-28
Hello. I'm trying to make ubuntu install over and remove windows 7.

My problem is this:
Error informing the kernal about modifications to partition /dev/sda1

This came after I was in windows 7 last night and made ubuntu its own partition.

Now Windows 7 will not start, and I'm unable to install ubuntu. 

Any suggestions? Windows won't even boot from my recovery disk.

---

### Post by lindsay7 on 2012-08-28
Use the live cd Ubuntu disk and then use Gparted to reformat the drive and partition it as you like. Then use the live cd to install Ubuntu.

---

### Post by Mark Phelps on 2012-08-29
Without seeing your partition layout, I'd have to guess ... but in preinstalled Win7 systems, the first partition on the drive is often the Win7 "boot" partition, which, if it is the typical size (couple hundred MB) is way to small for an Ubuntu install even if you reformat it.

Also, you say you want to install OVER Win7, but yet, you created a separate partition for Ubuntu.

If you really want to remove Win7, then booting from a LiveCD/Live  USB and using GParted to remove the partitions is the way to go.

---

