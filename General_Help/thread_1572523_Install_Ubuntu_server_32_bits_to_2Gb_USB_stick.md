---
title: "Install Ubuntu server 32 bits to 2Gb USB stick"
date: 2010-09-11
forum: General Help
---

### Post by dolphs on 2010-09-11
Dear linux friends,

I installed recently Ubuntu 10.04 32 bits server CD to USB stick (EXT4). The target machine is an 500Mhz VIA Epia Pico-ITX equipped with 1Gb of memory. This x86 server will run one or two processes 24/7 actively in memory. Therefore not too many writes to disk, maybe once or twice a week editing config files. Also I compiled the latest vanilla kernel, 2.6.35.4 atm, and optimised for VIA C3. However I like to limit my question in this thread to limit disk writes on USB stick, please let me know if you know other good tweaks to apply I did not find (overlooked) here.

Currently my USB stick shows:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             2.0G  1.1G  844M  57% /

Before posting this thread I googled a little and applied some enhancements already:  

tune2fs -O ^has_journal /dev/sda1
tune2fs -c 0 -i 0 /dev/sda1

vi /etc/sysctl.conf ( and add these lines )
vm.swappiness = 0
vm.dirty_background_ratio = 20
vm.dirty_expire_centisecs = 360000 # 1 hour
vm.dirty_ratio = 80
vm.dirty_writeback_centisecs = 0


vi /etc/fstab
---
UUID= /[blahbla] ext4  noatime,nodiratime 0 1
tmpfs /tmp       tmpfs defaults,size=32M 0 0
tmpfs /var/log   tmpfs defaults,size=32M 0 0
tmpfs /var/run   tmpfs defaults,size=32M 0 0
tmpfs /var/tmp   tmpfs defaults,size=32M 0 0

---

### Post by Gunman1982 on 2010-09-11
I read on this page: [http://wiki.archlinux.org/index.php/Acer_Aspire_One#File-systems]("http://wiki.archlinux.org/index.php/Acer_Aspire_One#File-systems")     that you can use ext2 or xfs instead of ext4 to go easier on the write operations.

---

### Post by dolphs on 2010-09-11
thanks for that tip, however I will stick with EXT4 for the moment, especially also as I ran "tune2fs -c 0 -i 0 /dev/sda1" which disables disk integrity checks that normally occuring every so many mounts ( 35? ). and disables also disk integrity checks that normally occuring every half year. Will keep an eye on XFS though, thanks for the tip!

---

### Post by dcstar on 2010-09-11
> **dolphs said:**
> thanks for that tip, however I will stick with EXT4 for the moment, especially also as I ran "tune2fs -c 0 -i 0 /dev/sda1" which disables disk integrity checks that normally occuring every so many mounts ( 35? ). and disables also disk integrity checks that normally occuring every half year. Will keep an eye on XFS though, thanks for the tip!

Disk checks are trivial, the ongoing writes of normal operation will kill the USB device 10,000 times more quickly than disabling those.

SSDs are designed (and are more expensive) for good reasons, you know.

---

### Post by dolphs on 2010-09-12
I know SSD is there also to limit wear and tear but that is simply no option here I have to stick with USB. So in order to disable journaling on EXT4 I executed "tune2fs -O ^has_journal /dev/sda1", this would save more disk writes. 
As said XFS is worth a try too. However I am just interested to get a stable system that won't panic when there is a power cut, manual reboot, etc. This panic is my experience with EXT2, therefore I decided to go for EXT4 this without journaling and without checking, maybe I should reconsider that last part (tune2fs -c 0 -i 0 /dev/sda1).

Also:
rm -f /etc/blkid.tab*
ln -s /dev/null /etc/blkid.tab
rm -f /etc/mtab
ln -s /proc/mounts /etc/mtab

current fstab:
UUID=id / ext4efaults,data=writeback,noatime,nodiratime, errors=remount-ro,commit=240  0 1

---

### Post by Someone1 on 2011-02-09
Yes, this is a bit old...
but how did you manage to install the server on a stick? My setup ran through just fine (took ages though...), but I couldn't boot from the stick. Tried two different ones. I got another one, thats currently in use, that is bootable for sure - will try that one next...

/edit: just tried the other stick and not even that one works. :( Is there some hidden option to make the installation "work" on a USB stick? Tried reinstalling GRUB from the install disc, didn't work though.

---

### Post by Someone1 on 2011-02-16
So since no one answered so far: I tried booting manually using the grub from my currently installed Ubuntu 8.04. Found the USB stick, but fdisk lists errors:
> 
Disk /dev/sdb: 8027 MB, 8027897856 bytes
247 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 15314 * 512 = 7840768 bytes
Disk identifier: 0x0007933b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         957     7323648   83  Linux
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 32, 33) logical=(0, 33, 3)
Partition 1 has different physical/logical endings:
     phys=(911, 224, 17) logical=(956, 147, 46)
Partition 1 does not end on cylinder boundary.
/dev/sdb2             957        1024      514048   82  Linux swap / Solaris
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(911, 224, 18) logical=(956, 147, 47)
Partition 2 has different physical/logical endings:
     phys=(975, 223, 16) logical=(1023, 180, 58)
Partition 2 does not end on cylinder boundary.

Running fsck and badblocks didn't help. Grub fails with error 13 (using chainloader +1) or error 16 (using kernel).

My next guess is to backup the files, manually format the USB stick and re-copy the files. Since grub doesnt work from the stick anyway that probably wont do any damage?
Well if that doesnt work I'll try the CompactFlash disc as soon as it arrives...


/edit: nope, didn't help a thing. No more errors in fdisk but still the same errors in grub.

---

### Post by Someone1 on 2011-02-20
Guess it was due to Grub Legacy... anyway I got my CF card + IDE adapter yesterday and installed. Just when I thought it wouldnt boot again I reinserted the install USB stick just to notice I had installed grub on that stick instead of the CF card ^^'. Works fine now.

---

### Post by 3rdalbum on 2011-02-20
Just to let you know, you'll probably still kill the USB stick within a year. Mine died within 6 months; admittedly I was running Ubuntu Desktop, but USB flash drives just aren't meant for this kind of use. Even a laptop HDD will work longer.

---

### Post by Kalmake on 2011-03-13
> **3rdalbum said:**
> Just to let you know, you'll probably still kill the USB stick within a year. Mine died within 6 months; admittedly I was running Ubuntu Desktop, but USB flash drives just aren't meant for this kind of use. Even a laptop HDD will work longer.

When the stick "died", what exactly happened? Were you just unable to write on it, or something worse?

---

