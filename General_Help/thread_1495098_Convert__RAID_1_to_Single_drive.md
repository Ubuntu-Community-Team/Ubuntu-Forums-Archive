---
title: "Convert  RAID 1 to Single drive"
date: 2010-05-27
forum: General Help
---

### Post by bakegoodz on 2010-05-27
I kept my movies on a 2 drive software raid1 mirror, but now I changed my mind about needing a raid and pulled one of the drives for another use. Can I convert the remaining raid drive back to a regular single drive and keep the data in place? Can I change the raid partition back to regular partition and be able to mount it?

---

### Post by dcstar on 2010-05-27
> **bakegoodz said:**
> I have 1 drive that was part of a two drive mirror (Software Raid 1) Right now I have to manual start it with mdadm before mounting it. Can I change the raid partition back to regular partition without copying the data back and forth? (1 TB of data)

RAID 1 is mirroring, there is no need to copy data from identical drives.

---

### Post by bakegoodz on 2010-05-28
I revised my question since you completely misunderstood what I was saying.

---

### Post by bakegoodz on 2010-05-30
Bump

---

### Post by sdennie on 2010-05-30
Why not just leave it as a degraded mirror?  I'm reasonably sure that there is no performance penalty for running a RAID1 array like that and, in the future, if you decide to add the redundancy back, it's trivial.

---

### Post by bakegoodz on 2010-06-01
I moved the drive to another computer and I have to manually start the degraded raid with mdadm before I can mount it.

---

### Post by dancho on 2011-04-22
I think that you can get rid of the RAID like this. Boot from a LiveCD of some sort (say Ubuntu 10.04). Let's say the drive that the mirror lives on is /dev/sda. Then in a terminal:

sudo apt-get update
sudo apt-get install mdadm
sudo modprobe md_mod
sudo modprobe raid1
sudo modprobe raid10 # In case you have RAID10 instead of RAID1

mdadm --zero-superblock /dev/sda # Destroys the md superblock

# Let's say your root partition is /dev/sda1. If not, replace sda1 with whatever it is.

mount /dev/sda1 /mnt

# If you have separate /boot, /usr/, and /var, mount them at this point, e.g.:

mount /dev/sda5 /mnt/usr # and similarly for the others.

chroot /mnt
rm /etc/mdadm/mdadm.conf
mount -t proc none /proc
mount -t sysfs none /sys
mount -t devtmpfs none /dev

grub-mkconfig > /boot/grub/grub.cfg
grub-install --recheck /dev/sda

# Now, edit your /etc/fstab, and make sure that there are no references to /dev/md devices, i.e. that all entries are either /dev/sdaN or UUID=XXXXXXXXXXXXXXXX


Now, reboot, and make sure the system is trying to boot from the drive you were just working on (in this case /dev/sda).

If you ever change your mind, you can use my guide to re-convert your system to a mirrored drive setup:

[http://iiordanov.blogspot.com/2011/04/how-to-convert-your-single-drive-linux.html](http://iiordanov.blogspot.com/2011/04/how-to-convert-your-single-drive-linux.html)

---

