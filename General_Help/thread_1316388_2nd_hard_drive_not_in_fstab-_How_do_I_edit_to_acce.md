---
title: "2nd hard drive not in fstab- How do I edit to access hard drive?"
date: 2009-11-05
forum: General Help
---

### Post by sofasurfer on 2009-11-05
I used to access my 2nd drive but now I can not. It appears that it is not listed in my fstab file. Where'd it go? Is that possible?

Been a long time since I messed with fstab. It became confusing when "uuid" entered the picture.

The 2nd drive shows up in my "Places" but I am unable to mount it.
I can boot to 2bd drive after changing boot options in BIOS.

The 2nd drive is dev/sdb5 (2nd operating system) and dev/sdb2 (storage).

How should I now edit my fstab for 2nd drive access?

Heres my current fstab...

```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=a28b4034-1a35-4618-baab-da0706b9d214 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2bc733de-79df-41d4-8c0d-aaa41d36b210 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by etnlIcarus on 2009-11-06
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

It would help, if you could tell us what the partitions are formatted as.

---

### Post by sofasurfer on 2009-11-06
Heres my Gparted data...

First drive (normally used)...

/dev/sda1               ext3      /       230 GB
/dev/sda2   extended                      2.8 GB
  ../dev/sda5   swap                        2.8 GN

Second drive (This is what I am trying to access)...
/dev/sbd1   extended                    130 GB
 ../dev/sdb5   ext3                        127 GB
  ../dev/sdb6   swap                        2.8 GB
/dev/sdb2   ext3                        167 GB

---

### Post by sofasurfer on 2009-11-06
Thanks for the links you gave me. I have not done any linux work in quite a while and I forgot where to find good info or even what I should be looking for.

---

