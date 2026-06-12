---
title: "Broken LVM after gparted renamed partitions that were PVs"
date: 2011-06-26
forum: General Help
---

### Post by viktorzk on 2011-06-26
Hello,

My harddisk had one extended partition, sda2, split into several logical partitions: sda6,sda5,sda7,sda8,sda9 in this order.  sda6,sda8,sda9 were [the only] PVs in one [and only] volume group.

I tried to delete sda7 and to resize sda5 (both unrelated to the LVM setup) to take the freed space. I entered both changes in GParted and clicked 'apply'. It gave some error, but had apparently deleted sda7, without resizing sda5. I tried to resize sda5 again, it again gave an error again, but sda5 was resized. I did not save any logs from GParted. Then I saw that the partition names had changed to sda8,sda5,sda6,sda7, in this order.

Now when I run 'vgdisplay', I get the error "Couldn't find device with uuid ....". Running 'blkid' gives the uuids of sda5,sda7,sda9. According to GParted and fdisk, sda9 does not exist. Also, according to blkid, the uuid of sda7 is what used to be the uuid of sda8. I am very confused.

As you could expect, I don't have backups, so... Help! (I am now creating a copy of the whole disk, in case things go even more wrong)

---

### Post by viktorzk on 2011-06-27
bump

EDIT: I'm writing this after the post below - there is just no point bumping this thread again. The problem is gone, I have no idea how or why. One reboot didn't change anything, but after the 2nd reboot suddenly fdisk and blkid agree on the new partition names, and lvm works fine.

---

### Post by srs5694 on 2011-06-28
Part of what's going on is normal. The numbers of logical partitions are not fixed; they're defined (and numbered) in a chain, and if you remove one link in that chain, the partitions after that one will all be renumbered. Thus, when you removed /dev/sda7, /dev/sda8 became the new /dev/sda7 and /dev/sda9 became the new /dev/sda8.

It's unclear to me why some of the other orders changed, but your use of descriptive text rather than the actual output of utilities like fdisk or blkid is also an impediment. (Of course, I realize you can't produce a "before" picture except through descriptive text, but you could post the output of "sudo blkid" and "sudo fdisk -lu" for your system as it is now.)

You might want to read the man page for pvck; it's a utility to check the metadata in a physical volume, and if a PV has been damaged on your system, it's conceivable it could help.

---

