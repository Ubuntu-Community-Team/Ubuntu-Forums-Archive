---
title: "Volumes still visible on desktop, 9.10"
date: 2009-11-10
forum: General Help
---

### Post by jstar10 on 2009-11-10
Hey all,

I do not want mounted volumes being displayed on my desktop.. I've fixed this before by using the gconf-editor tool to uncheck the "volumes_visible" property and this has worked in 9.04 and below. However, this property doesn't seem to do anything in my clean install of 9.10 -- the mounted drive still displays on my desktop and I don't know how to get rid of it. Anyone else having this problem? Is there another workaround? I've tried rebooting, restarting nautilius and double-checking the volumes_visible option was actually cleared -- no luck :(

Any suggestions? Thanks in advance!

---

### Post by hal8000 on 2009-11-10
Let's see what's mounted on your system.
Post the output of

mount


and also

cat /etc/fstab

---

### Post by jstar10 on 2009-11-10
mount output:

> /dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/umass/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=umass)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

cat /etc/fstab/

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=43823517-c39d-47ff-8706-04ef0c94e53a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=52620cd9-2cd4-4e97-9370-056d1a9183d3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


However, the volume that is showing up on my desktop is a WebDAV davs://xxx/ "volume".

I noticed that in 9.04 and earlier, using gconf-editor to disable volumes_visible updated the /.gconf/apps/nautilus/desktop/%gconf.xml file. However, this file doesn't exist (and isn't created or updated) when I use gconf-editor in 9.10. Where is this setting being held in 9.10? Is this why it appears to be broken?

---

