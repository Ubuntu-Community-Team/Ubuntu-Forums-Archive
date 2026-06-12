---
title: "eBox install - drive errors when booting"
date: 2011-03-17
forum: General Help
---

### Post by flycast on 2011-03-17
I have a Dell Dimension 690 with a LSI raid controller. I just added two 2Tb drives to the 2 160Gb drives that I currently have. The 160Gb drives used to be set up in a redundant raid configuration and are now set up as stand alone drives. The 2Tb drives are redundant raid.

I installed Zentyal server software (formally eBox). It seems that the system is starting up OK but on booting I am getting the following errors:
> ata_id[643]: HDIO_GET_IDENTITY failed for '/dev/sdb'
ata_id[642]: HDIO_GET_IDENTITY failed for '/dev/sda'
And then at the end of the boot log:
> certutil: function failed: security library: bad database.
sed: -e expression #1, char 17: unknown option to `s'
Stopping X display manager: slim not running (/var/run/slim.lock not found).
Starting X display manager: slim.
Starting X display manager: slim already running.
I do not want to put data files back on the server if it has some errors that will bite me later.

Any ideas on these two sets of errors?

---

### Post by flycast on 2011-03-17
This might be helpful...here is my fstab
> sorry, I posted the wrong fstab...the real one is below.


---

### Post by flycast on 2011-03-17
Sorry...here is the real fstab file...#-o:!:
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/sys-root /               ext4    errors=remount-ro 0       1
/dev/mapper/sys-boot /boot           ext2    defaults        0       2
/dev/mapper/data-home /home           ext4    defaults        0       2
# /mnt/backup was on /dev/sdb1 during installation
UUID=826f4181-be7f-4160-8e40-c811ad178c84 /mnt/backup     ext4    defaults        0       2
/dev/mapper/data-var /var            ext4    defaults        0       2
/dev/mapper/sys-swap none            swap    sw              0       0


---

