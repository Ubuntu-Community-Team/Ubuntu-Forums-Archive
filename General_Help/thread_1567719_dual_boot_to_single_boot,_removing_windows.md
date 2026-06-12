---
title: "dual boot to single boot, removing windows"
date: 2010-09-04
forum: General Help
---

### Post by jiggling_john on 2010-09-04
Hi all

I've got a win7/ubuntu 10.04 dual boot running on my system. I did the usual of installing 7 first, then ubuntu and using it as the default boot option.

I now want to get rid of win 7 and expand the ubuntu installation into the free space. My current hdd structure is in the attachment. If I just boot a live cd and gparted to remove the win 7 partitions and expand the ubuntu installation into the free space, will that work or will it have a massive panic?

Also, how to I get grub to silently boot after without offering me any boot options?

---

### Post by JedMeister on 2010-09-04
> **jiggling_john said:**
> If I just boot a live cd and gparted to remove the win 7 partitions and expand the ubuntu installation into the free space, will that work or will it have a massive panic?I would imagine it should work fine. You may need to do a 2 step process to extend your Ubuntu partition, first move the start of the extended partition (after deleting sda1&2) then grow the size of your ext4 partition. 

To be on the safe side **always** backup data you want to keep prior to any disk intensive stuff like that! (Just in case something goes wrong).

> **jiggling_john said:**
> Also, how to I get grub to silently boot after without offering me any boot options?Once you reboot, updating GRUB should fix that - assuming its GRUB2 (not sure about GRUB legacy - you may need to manually edit the config file).

---

### Post by jiggling_john on 2010-09-04
right o, i'll give that a bash now then. How do I update grub? *stupid question mode* :-p

---

### Post by 73ckn797 on 2010-09-04
Grub 2 info: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by jiggling_john on 2010-09-04
ok so i totally broke it...

I rebooted, did a gparted, deleted win partition, moved everything across and resized.

All seemed well

i had

sda3
 -sda5 system
 -swap


After that it wouldn't boot, just a flashing cursor so I rebooted into live usb and tried to reinstall grub.

I mounted /dev/sda5 and installed grub to there.

oh dear... this now seems to have killed my partition table? If i go into gparted now it says "invalid partition table on dev/sda - wrong signature 820"

any ideas how to rescue me?

---

### Post by jiggling_john on 2010-09-04
did it!

right, i dunno what i did wrong! I think when I resized the partitions there was no longer an active/boot partition. I ended up doing the following...

read this
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

then i downloaded and ran TestDisk

This is a bit of genius, it recovered my partition and re-wrote the partition table. I selected at this point to turn it into a boot partition.

The swap space disappeared somewhere...

I then followed instructions to reinstall grub

This worked!

After booting into my rescued installation, i used gparted to create a swap space where it used to be, used mkswap to set it and then edited my fstab to replicate the changes.

bit of a bugger all that but im back now and going to buy a back up hdd!

---

### Post by oldfred on 2010-09-04
You are too quick. But I am glad you got it worked out.

I generally recommend that you do not move partitions left as that has slightly more risk as you are copying/moving all the data. I prefer that you use the space for /home or for a /data partition and leave / (root) where it is.

Just for future info:

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

I like to keep a small system partition(s) and have data on separate partitions. Then it is easily to do full new installs to another system partition (keeping old for a while). I have several 20-25GB system partitons for new versions or testing.

---

### Post by JedMeister on 2010-09-05
Glad you got it all sorted in the end. And sorry if my "no worries" attitude lead you astray. Ah yes boot partition. I overlooked that. I would imagine that GParted should have been able to sort all that and while booted from a live CD/USB you should've been able to fix GRUB at the same time. GRUB should've warned about that at the time. Anyway, alls well that ends well I guess.

PS I've would've got the backup drive first! Better late than never though!

---

