---
title: "Need some help with swap partition"
date: 2011-03-04
forum: General Help
---

### Post by bongorider on 2011-03-04
I created a dual boot with windows 7 starter and ubuntu netbook remix, but this is my first time experimenting with linux and I totally misunderstood what a swap partition was for, and gave over 80% of my HD to the swap drive.  

I went back into windows 7 and deleted the partition and split it into 2 parts, intending to use 2GB for a swap partition.  How do I tell Ubuntu to ignore the previous designated swap partition (which no longer exists) and consider this new 2GB partition as the swap file?  I've read some FAQs which guide you through adding additional swap space or increasing the swap file size etc, but I'm so unfamiliar with Linux and Terminal commands that I can't figure out how to adapt that to my purposes.

---

### Post by Krytarik on 2011-03-05
Update your fstab and initramfs by following those guides:
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

If you did not already boot since re-arranging your swap: You will get an error message upon boot about it, but your sytem should nevertheless work, then follow the steps mentioned in the guide.

---

### Post by coldraven on 2011-03-05
Or maybe try booting with your Ubuntu Live CD.
Select "Try Ubuntu".
Run System>Admin>Gparted Partition Editor
Select your 2GB partition
Right click on it and select "format as Linux Swap"
Click "Apply", the green tick on the top panel.
When done, quit and shutdown, remove the CD.
I'm not an expert but that should help.

---

### Post by vanadium on 2011-03-05
It is not quite clear to me what you exactly did, but if your Ubuntu system is still intact except for the swap, editing your /etc/fstab configuration file should be all you need to restore the system. If you boot into your Ubuntu system, run following commands and post the output here, we can tell what needs to be adjusted.

```

sudo blkid
cat /etc/fstab

```

---

### Post by Krytarik on 2011-03-05
Oh yeah, +1 for formating the new partition as swap, if your partitioning tool didn't do that already.

And the update of initramfs is necessary to be able to "resume" after hybernating.

---

### Post by vanadium on 2011-03-06
> **Krytarik said:**
> 
And the update of initramfs is necessary to be able to "resume" after hybernating.
I see it now, thanks!

---

