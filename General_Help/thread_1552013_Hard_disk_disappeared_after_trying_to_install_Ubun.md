---
title: "Hard disk disappeared after trying to install Ubuntu"
date: 2010-08-13
forum: General Help
---

### Post by mohitdaksh on 2010-08-13
Ok, I guess I am going to be in some deep trouble. I tried to remove XP partition that was on my computer and install ubuntu. But the installation ended due to a power failure just after removing XP paritions I guess. Now, my IDE hard disk is not even getting detected. First I thought I have lost my hard disk, Now I have a little hope after seeing this <see attachments>
Is there a way to recover the partitions?

---

### Post by Rubi1200 on 2010-08-13
Hi,
sorry to hear about your problem.

Ok, to get a better idea of your setup and what is recognized, please use the Ubuntu CD to boot the computer. 
Choose the option to try in live mode.
At the Desktop, connect to the Internet.
Click on the link at the bottom of my post and follow the instructions there.
Post the results back here.

---

### Post by UberStudent on 2010-08-13
*First things first.* 

Plug in an external harddrive, boot into a Live Linux disc of some sort, navigate with root access to the drive...and get your needed files out of there!

---

### Post by mohitdaksh on 2010-08-13
@UberStudent 
I had backed up everything so data isn't a problem. I am just worried about the hard disk.


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================


=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)

=======Devices which don't seem to have a corresponding hard drive==============

sda 
=============================== StdErr Messages: ===============================

ERROR: asr: seeking device "/dev/sda" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sda" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sda" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sda" to 4608
ERROR: hpt45x: seeking device "/dev/sda" to 18446744073709545984
ERROR: isw: seeking device "/dev/sda" to 18446744073709550592
ERROR: isw: seeking device "/dev/sda" to 18446744073709551104
ERROR: isw: seeking device "/dev/sda" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sda" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sda" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sda" to 18446744073709550592
ERROR: pdc: seeking device "/dev/sda" to 137438913024
ERROR: pdc: seeking device "/dev/sda" to 137438920192
ERROR: pdc: seeking device "/dev/sda" to 137438927360
ERROR: pdc: seeking device "/dev/sda" to 137438934528
ERROR: sil: seeking device "/dev/sda" to 18446744073709551104
ERROR: via: seeking device "/dev/sda" to 18446744073709551104
ERROR: asr: seeking device "/dev/sda" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sda" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sda" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sda" to 4608
ERROR: hpt45x: seeking device "/dev/sda" to 18446744073709545984
ERROR: isw: seeking device "/dev/sda" to 18446744073709550592
ERROR: isw: seeking device "/dev/sda" to 18446744073709551104
ERROR: isw: seeking device "/dev/sda" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sda" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sda" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sda" to 18446744073709550592
ERROR: pdc: seeking device "/dev/sda" to 137438913024
ERROR: pdc: seeking device "/dev/sda" to 137438920192
ERROR: pdc: seeking device "/dev/sda" to 137438927360
ERROR: pdc: seeking device "/dev/sda" to 137438934528
ERROR: sil: seeking device "/dev/sda" to 18446744073709551104
ERROR: via: seeking device "/dev/sda" to 18446744073709551104

---

### Post by Rubi1200 on 2010-08-13
Hi mohitdaksh,

First, good that you backed up everything!!

Second, take a look here: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I have seen many people recommend testdisk here on the forums, but of course it is your choice.

Let us know if you need more help or if anything is unclear.

By the way, to answer the original question:

This is not a good sign: > no valid partition table found

But, as I said, you have some options available.

---

### Post by mohitdaksh on 2010-08-13
Thanks for your help.. I am trying that link now. I hope everything becomes fine

---

### Post by mohitdaksh on 2010-08-13
Just one more thing.. Can it happen just while trying to install ubuntu, or the hard disk is faulty?? Just your opinion

---

### Post by Rubi1200 on 2010-08-13
> **mohitdaksh said:**
> Just one more thing.. Can it happen just while trying to install ubuntu, or the hard disk is faulty?? Just your opinion
At this point, I cannot really say. But, I think a power failure could definitely mess things up!

Hopefully, testdisk (or whichever option you choose) will tell you if the disk is physically damaged. Just remember to do all this from the live cd as instructed there.

---

### Post by mohitdaksh on 2010-08-13
testdisk is showing only the CD drive not the hard disk.. I guess I am gone.. :(

---

### Post by Rubi1200 on 2010-08-13
Did you try this?

[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by Nick_Jinn on 2010-08-13
Sometimes I have had storage that was not detected by Windows or Ubuntu, but Knoppix by some black art was able to detect it. You might want to try running Gparted from Live Knoppix disk. Knoppix is not nearly as functional for daily use, but it is the best live distro for trouble shooting problems with your other operating systems.

---

