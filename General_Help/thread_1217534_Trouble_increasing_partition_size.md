---
title: "Trouble increasing partition size"
date: 2009-07-19
forum: General Help
---

### Post by AustenB on 2009-07-19
Hi, I recently installed the latest version of ubuntu today, and I've ran into an issue with the update manager:  Update manager doesn't have enough room to install on the disk.  I've actually seen other threads with my exact same problem, but I don't want to clutter their thread, so I made my own.  I've created a gparted live CD and booted from it to increase the size of my linux partition, but it says its capped at 2.32 GiB and won't let me increase it, even if I shrink other partitions and make room for it.  Do I have to reinstall ubuntu and increase the linux partition?  If so that seems kinda careless, because the default setting for the partition size shouldn't be set to a value that's too small

I'd upload a ss, but my disk can't save it cause there's not enough space at this time.

---

### Post by michy99 on 2009-07-19
Your Ubuntu partition may be inside another extended partition that has to be expanded first. Also, make sure that all partitions are unmounted and that swap is turned off.

What is the output from this command?```
sudo fdisk -l
```

---

### Post by AustenB on 2009-07-19
Thx for the help, this is the output

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x683fbc96

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10490413+  27  Unknown
/dev/sda2   *        1307       15854   116854784    7  HPFS/NTFS
/dev/sda3           15854       30076   114233528    7  HPFS/NTFS
/dev/sda4           30077       30401     2610562+   5  Extended
/dev/sda5           30077       30379     2433816   83  Linux
/dev/sda6           30380       30401      176683+  82  Linux swap / Solaris

```

---

### Post by michy99 on 2009-07-19
/dev/sda4 is an extended partition which contains the two logical partitions /dev/sda5 and /dev/sda6. Expand /dev/sda4 first and then you can expand /dev/sda5 inside it.

---

### Post by AustenB on 2009-07-19
Ya, gparted says sda5 and sda6 are both in sda4, but I couldn't increase sda4 either, but I don't think I swappedoff, I'll boot from cd and try that again i guess, but what would you recommend as to how big the partitions should be resized to?  Btw it's dualboot with win vista.

edit: k thx i'll try

---

### Post by michy99 on 2009-07-19
I would make the Ubuntu partition at least 10 Gig. Also you may have to make a change to your fstab file since you are changing the starting point of sda5. What does your fstab file look like?```
cat /etc/fstab
```

---

### Post by AustenB on 2009-07-19
Okay so I partitioned the disk; you can see it in the attachment. As far as my fstab, I don't really know what it is, but it doesn't look pretty :/

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=ebc72e5e-2929-40d9-bc63-89b545e43967 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=95c0b81e-590a-4086-87f0-1fce1826097a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by CatKiller on 2009-07-19
The UUID of the ext3 partition won't change with moving the startpoint of that partition, but I think that the swap partition gets destroyed and recreated rather than moving it. You can find the UUID of the new swap partition with ```
sudo vol_id -u /dev/sda6
``` You can then put that number in place of the existing one for your swap partition with ```
gksudo gedit /etc/fstab
``` and then enable swap again with ```
sudo swapon -a
```

---

### Post by AustenB on 2009-07-19
Sorry,I got the new UUID, but I'm not really sure what you're saying to do in the second step.  When I put in ```
gksudo gedit /etc/fstab

``` a new window pops up that's editable, which says:```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=ebc72e5e-2929-40d9-bc63-89b545e43967 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=95c0b81e-590a-4086-87f0-1fce1826097a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```  Do you want me to replace the first or second UUID in this window?

edit: I notice now the second one is the same as the one I retrieved, but just to confirm, you want me to replace the first one then?

---

### Post by michy99 on 2009-07-19
If it is the same, then it is ok. It would be the one under the line that says swap. (The second one) The main question is does the computer boot up into Ubuntu now like it should?

---

### Post by AustenB on 2009-07-19
Ya the computer boots up fine, there's about 10 Gigs in the root, and the UUID is the same for the swap, so I think I'm good.  Thanks a lot guys.

---

