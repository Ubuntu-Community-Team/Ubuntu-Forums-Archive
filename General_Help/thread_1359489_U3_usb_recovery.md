---
title: "U3 usb recovery"
date: 2009-12-19
forum: General Help
---

### Post by WuMing on 2009-12-19
Greetings, I'm having a problem with recovering data from a sandisk usb with U3 protection enabled. My brother lost the password, and I thought I could recover it by using dd to image the device and extract the password out of the data... However only the U3 application shows up when ls -l /dev/disk/by-id/usb* is used. I read somewhere that the U3 security application does something with partitions (e.g. U3 boots first then the main partition). So I tried to look for a second partition on the device (it has no second partition). 

Sorry for the long winded intro, but I'm at a loss as to how to get the data back and I really wanted to avoid using a data recovery serves &/or dealing with sandisk...

your help is greatly appreciated.

---

### Post by Darael on 2009-12-19
> **WuMing said:**
> Greetings, I'm having a problem with recovering data from a sandisk usb with U3 protection enabled. My brother lost the password, and I thought I could recover it by using dd to image the device and extract the password out of the data... However only the U3 application shows up when ls -l /dev/disk/by-id/usb* is used. I read somewhere that the U3 security application does something with partitions (e.g. U3 boots first then the main partition). So I tried to look for a second partition on the device (it has no second partition). 

Sorry for the long winded intro, but I'm at a loss as to how to get the data back and I really wanted to avoid using a data recovery serves &/or dealing with sandisk...

your help is greatly appreciated.
Hmm... try to find out what the stick's device ID is (/dev/sd<something>) and then run "sudo fdisk -l /dev/<whatever>" to find out what partitions are on it.

---

### Post by WuMing on 2009-12-19
output from ls -l /dev/disk/by-id/usb*
lrwxrwxrwx 1 root root 9 2009-12-19 17:21 /dev/disk/by-i /usb-SanDisk_Cruzer_Contour_0000168307734551-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 9 2009-12-19 17:21 /dev/disk/by-id/usb-SanDisk_Cruzer_Contour_0000168307734551-0:1 -> ../../sr1

sudo fdisk -l /dev/sr1
Note: sector size is 2048 (not 512)
Disk /dev/sr1: 25 MB, 25165824 bytes
255 heads, 63 sectors/track, 0 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes
Disk identifier: 0x00000000
Disk /dev/sr1 doesn't contain a valid partition table

and thats the output for sr1; sdb comes up with nothing.
sr1 is the partition for the U3.

(thanks for the reply)

---

### Post by jerrrys on 2009-12-19
found this

[http://www.fixya.com/support/t2929104-sandisk_cruzer_micro_3_gb_lost_password](http://www.fixya.com/support/t2929104-sandisk_cruzer_micro_3_gb_lost_password)

---

### Post by Darael on 2009-12-19
Ah! There are files on the stick, but it presents itself as a CD drive until... something... happens. You know this because "sr" devices are optical media drives. That means there is a way (though I don't know how) of making it switch modes. It may work to just unmount the volume presented without removing the stick. That's if the link jerrys provided doesn't do the trick.

---

### Post by WuMing on 2009-12-19
yes, I noticed that the Internet has very little information regarding this topic and the little that it does have seems to suggest its impossible without the password. A few posts even metioned that it has a lockout feture, which destroys the data if the wrong password is entered too many times. Also a password reset wipes the data too...

I'm wondering though, what would happen if I destroyed the partition that the U3 data is located on...

-------

No I tried unmounting the usb U3 partition; nothing changes... I also tried another suggestion that claims that the U3 application is controlled by an autorun script which would be disabled if you inserted the usb at boot up (that would be a really bad bug anyway).

---

### Post by Darael on 2009-12-19
I wouldn't be surprised if the actual data was encrypted. That would mean that you'd only be making the situation worse if you destroyed the U3 data - at least, if you didn't back it up first.

---

### Post by WuMing on 2009-12-19
most of the sources I found suggested that the data was unencrypted and that it was just partition manipulation that was securing the data, though the usb is relativity new so they could have made upgrades...

It has to be doing something with partitions because the only partition that shows up is the 25mb one with the U3 applications on it (its an 8GB usb).

---

### Post by Darael on 2009-12-19
> **WuMing said:**
> most of the sources I found suggested that the data was unencrypted and that it was just partition manipulation that was securing the data, though the usb is relativity new so they could have made upgrades...

It has to be doing something with partitions because the only partition that shows up is the 25mb one with the U3 applications on it (its an 8GB usb).

In that case, you cold try unmounting the U3 app partition and using testdisk to manipulate the partition table, potentially revealing any that are hidden and not placing the U3 app one in there... I don't know how viable that is, but in my experience testdisk is pretty versatile.

EDIT: Forgot to mention, testdisk is in the Ubuntu repos, with the package name "testdisk", strangely enough.

---

### Post by deathbyswiftwind on 2009-12-19
Id definatly recommend hitting your brother for this :lolflag:

---

### Post by WuMing on 2009-12-19
ok I tried testdisk on /dev/sr1 it says I its read-only (e.g. I can't do much of anything). Just out of curiosity if I delete the all partitions on the device would I still be able to recover the data after a reformat?

---

### Post by Darael on 2009-12-21
I'd advise against it - try running testdisk on /dev/sdb first, at least. Your chances of recovering the data are considerably slimmer of you reformat it.

---

