---
title: "External HDD not mounting"
date: 2009-07-31
forum: General Help
---

### Post by malel on 2009-07-31
I used to have my external HDD showing up in the Icons but now it does not . This has happened since some recent updates.
Doing 'fdisk -l' shows that the external HDD is recognised at SDB but it is not being mounted. How do I go about having this mounted.
Thank you

---

### Post by razorboy5 on 2009-08-01
well i'm not 100% if this applies here
however if it uses MTP perhaps u need to download it

check if u have mtpfs libmtp installed in synaptic

could be 100% off here thou, just speaking from experience
i have a mp3 device (which i guess is just another external HDD) 
and was being recognized but not being mounted.

---

### Post by scouser73 on 2009-08-01
> **malel said:**
> I used to have my external HDD showing up in the Icons but now it does not . This has happened since some recent updates.
Doing 'fdisk -l' shows that the external HDD is recognised at SDB but it is not being mounted. How do I go about having this mounted.
Thank you

You could try to use this tutorial: [[COLOR="Red"]**Ubuntu: Mount External Hard Disk**[/COLOR]]("http://www.blog.highub.com/linux/ubuntu-mount-external-hard-disk/")

---

### Post by malel on 2009-08-02
scouser73. What is there in that place you referred me to that I can get the required info ? Will give you a 1 out of 10 for that reply.
I am still having trouble with this External HDD. I see where others have had the same problem after an Upgrade/Security fix . Surely these are supposed to fix thing not BREAK them.
I have had a look in the /etc/fstab file and see that there is no entry there for SDB1. Some help in advising what I should enter there would be appreciated 

Thank you

---

### Post by merlinus on 2009-08-02
What is the filesystem, and mountpoint you created?

---

### Post by malel on 2009-08-02
The file system is  ext3 mount point is /media/sdb1

---

### Post by merlinus on 2009-08-02
Try this:

```
sudo mount -t ext3 /dev/sdb1 /media/sdb1
```

---

### Post by malel on 2009-08-02
Thank you merlinus but it tells me that /media/sdb does not exist. Looks like I might have got myself in a bit of a pickle here. Is there something else I can try ?

---

### Post by merlinus on 2009-08-02
```
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
```

I mistakenly assumed that you had already created the mountpoint.

---

### Post by malel on 2009-08-02
Thank you this is what I get 

mal@Pentium4:~$ sudo mkdir /media/sdb1
mal@Pentium4:~$ sudo mount -t ext3 /dev/sdb1 /media/sdb1
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

When I do 'dmesg | tail' I get the following

mal@Pentium4:~$ dmesg | tail
[ 7743.704367] atkbd.c: Unknown key pressed (translated set 2, code 0x8b on isa0060/serio0).
[ 7743.704370] atkbd.c: Use 'setkeycodes e00b <keycode>' to make it known.
[ 7743.883126] atkbd.c: Unknown key released (translated set 2, code 0x8b on isa0060/serio0).
[ 7743.883129] atkbd.c: Use 'setkeycodes e00b <keycode>' to make it known.
[ 7744.099283] atkbd.c: Unknown key pressed (translated set 2, code 0x8b on isa0060/serio0).
[ 7744.099286] atkbd.c: Use 'setkeycodes e00b <keycode>' to make it known.
[ 7744.232876] atkbd.c: Unknown key released (translated set 2, code 0x8b on isa0060/serio0).
[ 7744.232880] atkbd.c: Use 'setkeycodes e00b <keycode>' to make it known.
[ 7813.145018] VFS: Can't find ext3 filesystem on dev sdb1.
[ 7850.114162] usb 1-8: reset high speed USB device using ehci_hcd and address 4


When I do 'fdisk -l' I get the following

mal@Pentium4:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd722da6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1579    12683286   83  Linux
/dev/sda2            1580        9729    65464875    5  Extended
/dev/sda5            1580        9489    63537043+  83  Linux
/dev/sda6            9490        9729     1927768+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5ead3aca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   8e  Linux LVM

Does that show that the system filesystem is Linux LVM?

---

### Post by merlinus on 2009-08-02
Yes, and that is why having ext3 in the mount command did not work.  I do not know anything about LVM filesystems.  You might do a search on the forum and at google.

---

### Post by malel on 2009-08-02
Okay thank you very much for your help . I will keep working away at it.

Cheers

---

