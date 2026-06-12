---
title: "Installing gentoo after ubuntu?"
date: 2006-02-25
forum: General Help
---

### Post by Mantrasong on 2006-02-25
Hey all, I want to give gentoo linux a try (its a project for a computer course I'm in, to see if I can get it up and running), and I was wondering how to repartition my computer to set it up. I am already running Ubuntu and Windows on this machine. I was planning to use the System Rescue CD's gtparted to repartition, but when I booted it up to edit the partitions, this is the table I got:

```
HD 1 (80 gig)
/dev/hda1 39.19M fat16 (Dell boot partition)
/dev/hda2 55G NTFS (Windows XP)
/dev/hda3 20G Fat32 (Data)

HD 2 (200 gig) - Ubuntu install
/dev/hdb1 243Mb ext3 (Should be my swap(?))
/dev/hdb2 186Gb extended (Ubuntu)
     /dev/hdb5 186GB unknown (?)
```

I apologize that it isn't clearer, it's been a while since I installed ubuntu and I lost my write out of the partitions.

In any case, qtparted doesn't recognize anything about the extended partition, including how much of it I've used up, so I am rather wary of simply resizing it, but I do want gentoo on the second hard drive.

Does anyone have suggestions on how to repartition my hard drive to install gentoo safely without wiping out ubuntu in the process?

---

### Post by taurus on 2006-02-25
Take /dev/hdb5 and partition and divide that into two more partitions:  one for / (/dev/hdb5) and one for /boot (/dev/hdb6).  You can use the same swap partition for both Ubuntu and Gentoo.  When you get to the partition in the handbook about mounting your Gentoo, do

```

mkdir /mnt/gentoo /mnt/gentoo/boot
mount -t ext3 /dev/hdb5 /mnt/gentoo
mount -t ext3 /dev/hdb6 /mnt/gentoo/boot

```

And don't forget to turn your swap on as

```

swapon /dev/hdb1

```

---

