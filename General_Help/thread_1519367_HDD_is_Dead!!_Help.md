---
title: "HDD is Dead!! Help"
date: 2010-06-28
forum: General Help
---

### Post by tropdoug on 2010-06-28
I followed the sticky thread here on known issues with Lucid, specifically the issue with plymouth on boot up. Everything seemed ok, until this morning when the laptop simply will not boot. Using a live cd and gparted it seems the HDD is not there. 

Is there any fix or do I have to put the laptop into a shop to see if the HDD is dead. Up until now all has been fine with it, so why should those commands on the sticky have killed my drive?

---

### Post by cascade9 on 2010-06-28
Its probably coincience.  

Does the drive appear in the BIOS?

---

### Post by Rubi1200 on 2010-06-28
If you can use the LiveCD then boot the computer and post the results from the script in my signature here to the forum.

It will help us determine what is going on.

---

### Post by tropdoug on 2010-06-28
bootinfoscript just gives me 'command not found and the complete line [http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net) gives me no such file or directory?

---

### Post by tropdoug on 2010-06-28
Disregard the above, I am being a complete dodo. Just clicked your sig and copying the commands now. Will get back soon

---

### Post by tropdoug on 2010-06-28
ok the output is ```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================


=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
error: block: No such file or directory
error: devices: No such file or directory
error: /dev/mapper/no: No such file or directory
error: found: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

no block devices found 
```

I think my hdd is kaput!

---

### Post by gradinaruvasile on 2010-06-28
Is the drive listed in the laptop's BIOS?
You enter the BIOS BEFORE booting up with f2, or del (depends on the manufacturer) - you should see the key listed in the very first images that appear after powering on.

---

### Post by tropdoug on 2010-06-28
No - I went in and it says No HDD

---

### Post by cascade9 on 2010-06-28
Its dead, jim....er...tropdoug. BTW, sounds like you should be in townsville.

---

### Post by tropdoug on 2010-06-28
Yup - its dead. Pooh bah! Hmmmm my thinking is on a par with being in Townsville for sure --- slow and labored and a little incorrect LOL. 

maybe thats what happens after a long wet season -- mushy head. Thanks for the help guys

---

### Post by cascade9 on 2010-06-28
LOL

Sorry for you loss, but sometimes, hardware breaks. :(

---

