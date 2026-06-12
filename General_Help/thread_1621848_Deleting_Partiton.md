---
title: "Deleting Partiton"
date: 2010-11-14
forum: General Help
---

### Post by UltraAnders on 2010-11-14
Having purchased an SSD and installed Ubuntu on it, I'd like to delete my old Ubuntu install partition from my other HDD and expand the home folder. To do this, I'll need to move the linux-swap partition. "/boot" and "/" are on the SSD. Anything I need to watch out for?

GParted won't let me delete the partition and shows the message "Please unmount any logical partitions having a number higher than 5. 6 is swap and 7 is "/home" so I assume I'll need to use a liveCD to complete the task.

Thanks!

---

### Post by drs305 on 2010-11-14
A few things to watch:

Even on the LiveCD, all partitions must be umounted, including the LiveCD swap partition.
After you have made your changes and before you exit the LiveCD and reboot:
```
sudo blkid -c /dev/null
```
That will give you the current, non-cached UUIDs of your partitions.

Mount your new installation partition:
```
sudo mount /dev/sd**XY** /mnt
```

Make sure your fstab entries are correct before rebooting.
```
gksu gedit /mnt/etc/fstab
```

Install grub on the new partition (if you are in your new install, just run "sudo grub-install /dev/sdX". Change X to the drive designation and do not include the partition number.)

If you aren't in that install (i.e. you are still on the LiveCD while moving things about), I'll use sda5 in the example, change as necessary, and run:
```

sudo mount /dev/sda5 /mnt
sudo mount /dev/sdXY /mnt/boot  # change XY to your boot partition
sudo grub-install --root-directory=/mnt /dev/sda
```

After you are in your new install, make sure swap is working:
```
free -m
```

---

### Post by ibod on 2010-11-14
> **UltraAnders said:**
> Having purchased an SSD and installed Ubuntu on it, I'd like to delete my old Ubuntu install partition from my other HDD and expand the home folder. To do this, I'll need to move the linux-swap partition. "/boot" and "/" are on the SSD. Anything I need to watch out for?

GParted won't let me delete the partition and shows the message "Please unmount any logical partitions having a number higher than 5. 6 is swap and 7 is "/home" so I assume I'll need to use a liveCD to complete the task.

Thanks!

Yes use the live cd to boot while you modify the partitions 

do you intend to only have a /home on the hard drive and all else on the SSD

i am new to ubuntu my self but have installed it to many pc's this sounds ok to me but i would have set it all up at install time then you do not have to look out for any edits you will need to make if any, as all that will be done by the partition editor in the install sequance

---

### Post by UltraAnders on 2010-11-18
Hey hey, thanks both for your help. Using the 10.10 LiveCD worked a treat. Had to unmount (swapoff) the swap partition. Deleted other partitions, then moved and expanded the home partition. I mounted my existing 10.04 install partition but there was nothing in /mnt. So I took a punt and booted my system ... it worked. :)

As I've never had a good experience upgrading from one version of Ubuntu to the next I always just install the new version in another partition. What I was doing here was getting rid of 2 older installs (9.04 and 9.10 I guess).

Ibod, my current setup partition wise is:
On the SSD:
1 - 256mb (ext2), mount point: /boot
--then in the extend partition:
2 - 15gb (ext2), mount point: /
3 - the rest left spare for another OS or 2, probably 10.10 at some point.

On the HDD:
1 - 100gb (ntfs), Windows XP (not been used for months now I think about it)
--then in the extended partition:
2 - 2gb (linux-swap), mount point: /swap
3 - the rest (ext3), mount point: /home

One pain I've found with this setup is that each Ubuntu install has to use a different user name, as sharing home folders between installs isn't a good idea. I've seen mentioned a "/data" suggesting it could be used to share docs, music, etc. between installs, but I haven't been able to find much about it. Don't think I'd suggest my setup is optimal ;) but it works for me. There might be some sense in having "/home" on the SSD if "/data" works as I hope.

---

