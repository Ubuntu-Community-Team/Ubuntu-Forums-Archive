---
title: "Need help converting hard drive to ntfs"
date: 2011-12-03
forum: General Help
---

### Post by hinsonfan on 2011-12-03
I want to install windows 7 onto my laptop, and when I tried to, I received an error message saying windows can't install to the hard drive because the drive is not NTFS. I've searched on google and here and can't find out how to change it. I'm not worried about losing data as it's all been backed up. Please explain it to me like I'm a child, because I'm not very computer literate. Thanks.

---

### Post by raja.genupula on 2011-12-03
use disk utility or gparted . i support gparted . you can find many how to's on Gparted . by that you can do

---

### Post by hinsonfan on 2011-12-03
I tried it in disk utility which seems easy but it says I can't do it because the device is busy/mounted. I'll take a look at gparted. Thanks.

---

### Post by hinsonfan on 2011-12-03
Just stumbled across this identical situation posted back in Feb. I think i was afraid that the "delete partition" would mess up the hd. I may try this.

[http://ubuntuforums.org/showthread.php?t=1686620](http://ubuntuforums.org/showthread.php?t=1686620)

---

### Post by oldtimer7777 on 2011-12-04
> **hinsonfan said:**
> I want to install windows 7 onto my laptop, and when I tried to, I received an error message saying windows can't install to the hard drive because the drive is not NTFS. I've searched on google and here and can't find out how to change it. I'm not worried about losing data as it's all been backed up. Please explain it to me like I'm a child, because I'm not very computer literate. Thanks.

Boot from live disc of Ubuntu or usb live flash drive of Ubuntu.

Use gparted to delete your entire partition and reparition/format it to NTFS.  

If you need to install gparted it is:

sudo apt-get install gparted

It is actually very straight forward but you may need to research how to use gparted first. 

Goodluck

---

### Post by fdrake on 2011-12-04
> **hinsonfan said:**
> I want to install windows 7 onto my laptop, and when I tried to, I received an error message saying windows can't install to the hard drive because the drive is not NTFS. I've searched on google and here and can't find out how to change it. I'm not worried about losing data as it's all been backed up. Please explain it to me like I'm a child, because I'm not very computer literate. Thanks.

the suggestions from the prevous post should be enough. i just wanted to add that just deleting the partitions (and making all the hdd unloccated) should be enough for the win installation to start.

---

### Post by cap10Ibraim on 2011-12-04
you shouldn't be using (mounting) the partition that you want to edit or delete that's why you should use live-cd or live cd 
anyway the windows 7 installer also can delete or format them for you , I forgot the exact options but look around for something called custom or edit hard disk

---

