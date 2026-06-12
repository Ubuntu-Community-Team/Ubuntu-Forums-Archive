---
title: "Change location of /tmp to external HD"
date: 2009-11-01
forum: General Help
---

### Post by mustanglover32 on 2009-11-01
Ok, I have Ubuntu 9.10 up and running on my new SSD (sda5).  However, I want to change the location of my tmp directory to an external hard drive.  How do I do it?  I don't want to screw up my computer by messing around with the fstab file.

This ext hard drive is connected to the computer via USB, and is directory I want to send tmp to is here:
/media/EXTERNAL_HD/tmp

Here is what my fstab file looks like:  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=000252fb-4e9f-474f-ae4b-bc92194d5ab9 /               ext3    noatime,errors=remount-ro 0       1
# /dev/sda5
UUID=3d96d81d-41db-458e-9fbf-a40e55066bc4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Thanks,
David

---

### Post by rockstarrem on 2009-11-01
I don't know how else to do it besides reinstalling and making a new partition, then choose the mount point as /tmp. Theres probably another way though.

---

### Post by philippe_carlo on 2009-11-01
> **mustanglover32 said:**
> Ok, I have Ubuntu 9.10 up and running on my new SSD (sda5).  However, I want to change the location of my tmp directory to an external hard drive.  How do I do it?  I don't want to screw up my computer by messing around with the fstab file.

This ext hard drive is connected to the computer via USB, and is directory I want to send tmp to is here:
/media/EXTERNAL_HD/tmp

Here is what my fstab file looks like:  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=000252fb-4e9f-474f-ae4b-bc92194d5ab9 /               ext3    noatime,errors=remount-ro 0       1
# /dev/sda5
UUID=3d96d81d-41db-458e-9fbf-a40e55066bc4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Thanks,
David

Can you plug in the drive and post the output of 'mount' in a terminal window?

---

### Post by mustanglover32 on 2009-11-01
Here is the output of mount:

/dev/sdb1 on / type ext3 (rw,noatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/deberry/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=deberry)
/dev/sdc1 on /media/EXTERNAL_HD type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdd1 on /media/16-GB type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

---

### Post by mustanglover32 on 2009-11-04
bump.....

---

### Post by soapBAR2 on 2009-11-04
You can either make a link to it
sudo mv /tmp /mnt/externaldrive/tmp ; sudo ln -s /mnt/externaldrive/tmp /tmp

or change the environment variable

```
sh
sudo export TEMPDIR=/new/temp/dir

```

If you want to make the second one permanent and system-wide, put them in the /etc/profile (should apply to any sh-based environments) and reboot.

---

### Post by mustanglover32 on 2009-11-05
Wont' give me permissions to that directory on my external HD.  Can't edit permissions on external HD either probably because its FAT32, but that is just my guess.

---

### Post by mustanglover32 on 2009-11-06
bump

---

### Post by dcstar on 2009-11-06
> **mustanglover32 said:**
> Wont' give me permissions to that directory on my external HD.  Can't edit permissions on external HD either probably because its FAT32, but that is just my guess.

Linux system folders must be on filesystems that have full Linux support.

Mucking around with system folders is a great way to wreck your system.

---

### Post by mustanglover32 on 2009-11-06
> **dcstar said:**
> Linux system folders must be on filesystems that have full Linux support.

Mucking around with system folders is a great way to wreck your system.


Thanks for the honest answer.  In that case I will pick up another hard drive and format it for ubuntu. 

Thanks again,
David

---

