---
title: "Problems mounting External Drive"
date: 2010-03-07
forum: General Help
---

### Post by Ex-windows on 2010-03-07
I have a Seagate Freedesk external drive. I formatted it to ext3 (as per several posts regarding this)However I cannot mount the drive. If I go "places" "computer" I can see the drive (simply entitled USB Drive) but if I try to open it  it says "cannot mount the drive". If I right click and select "Mount Volume" I get Nothing. How can I get this to auto mount like other usb drives???
 I am using Hardy on a Compaq Laptop.

---

### Post by ram2500 on 2010-03-07
ext3 is supposed to work as it is a Linux native file system. However, has it worked before? Are there any files on the drive?

I am guessing your fstab file may not be correctly listing the hard drive. I have edited my fstab file many times, though I am no expert as circumstances vary widely. See if fstab is the problem.

---

### Post by Ex-windows on 2010-03-07
Thanks for the reply

Here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ff5a20fb-9322-4e74-91af-e551f6baadd9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=8548e315-e0a5-4813-9127-857b2e2ea6f3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sda1     /media/sda1             user,noauto,exec,utf8 0       0
# /dev/sdb1     /media/disk             user,auto,exec,utf8 0       0

The last line should be the usb. I  chenged the "noauto" to "auto" in hops of success. The Seagate drive should be sdb according to partition editor not sdb1.

HERE is my mtab

/dev/sda2 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-21-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/ravns3/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ravns3 0 0


The Seagate drive should be sdb according to partition editor not sdb1.
Not sure how to do what.

---

### Post by Ex-windows on 2010-03-13
I could sure use some help with this. tya

---

