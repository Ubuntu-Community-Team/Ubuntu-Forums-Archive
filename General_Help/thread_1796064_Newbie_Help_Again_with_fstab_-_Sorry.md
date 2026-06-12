---
title: "Newbie Help Again with fstab - Sorry"
date: 2011-07-03
forum: General Help
---

### Post by Quarkrad on 2011-07-03
I had a problem recently (could not mount a partition called **homefiles** and it appeared as **media/sda5** in nautilus) and corrected it with help from this forum - the end result was an fstab file looking like this:

 
[B]UUID=edad6a75-8cff-495b-95f9-d67037bb660a / ext4 defaults 0 1
UUID=EE80115F80113017 /media/WINXP ntfs-3g defaults 0 0
UUID=ae207b6d-9c06-4865-b0a4-4f3f16f60e25 /media/homefiles ext4 defaults 0 0
UUID=7726AB6749D7F693 /media/HFCopy ntfs-3g defaults 0 0
UUID=e928983b-2bc5-4b95-b692-a3999f2c217e swap swap sw 0 0
UUID=10144AE6144ACE82 /media/Images ntfs-3g defaults 0 0
UUID=E65C87295C86F399 /media/Backup ntfs-3g defaults 0 0[/B]

I haven't done anything since but I noticed today in Nautilus that I am not automounting my **homefiles** or **store** partitions. I had a look at fstab (expecting it to look as per above) but it now looks like this:

[B]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=0746a4a4-fa4d-422d-b82a-35d10699383b /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda6 during installation
UUID=7e66d7d5-2600-4c4a-9ad5-692ee4793675 none            swap    sw              0       0[/B]

This looks very odd to me - why is it so different and what's caused it to change by itself?  Is it wise for me to make a copy of fstab and replace it with the original above?  Will it not change again - it was working (automounting **homefiles**) OK but suddenly changed?

---

### Post by Quarkrad on 2011-07-04
I wrote another fstab file using UUID numbers for each partition obtained from 'information' using GPARTED.

---

