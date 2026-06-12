---
title: "all my NTFS partitions are suddenly and permanently read-only"
date: 2012-04-15
forum: General Help
---

### Post by wildwood on 2012-04-15
I'm fairly new to Linux (about 6 months) and have been using ubuntu for that time, and everything has been going great until yesterday. I tried to copy a folder of photos to an external USB HDD and was informed that it was short of a few GB to store the folder. I had just deleted about 20Gb of redundant files from it using a different ubuntu laptop and that had apparently succeeded. (except for not freeing up the space!).  I had used the drive previously for transferring data and nothing had changed except the installation of a few programs with software center. I decided to launch one of them - gparted - and see if it had any tools for this kind of cleanup. As it started all the partitions disappeared from the folder window I had open and then re-appeared. It didn't have any tools so I quit and tried again to copy the folder, but THIS time the message said it was a read-only filesystem.

I continued poking buttons and discovered that not only was the USB drive read-only but also the two NTFS partitions on the internal HD of my laptop, one for windows 7 and the other I use as shared storage between the two.

The FAT32 partition on the external drive was still writable.

I've done a fair bit of research since then but not fount an answer. something seems to have been changed in the process of re-enumerating the HDD's by gparted. I've removed gparted and nothing has changed. I've learned a bit about mount, fstab etc, but still confused by fuse.  I did a full surface scan and fix in win7 of the win7 drive, no change.

I've tried setting fixed mounts for the drives in fstab but I get a message saying there was a serious error checking them whilst booting up. They are still read-only.

the original fstab looked like this:

[I][B]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=fe581af8-ca36-49c2-b7e1-e4757f2c7ff1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=92a72981-5ce0-46e9-8c35-4f76677549a7 none            swap    sw              0       0
[/B][/I]
and with this, mtab looks like this:

[I]/dev/sda6 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/jeremy/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=jeremy 0 0
[B]/dev/sda3 /media/Data ntfs ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks 0 0
/dev/sda2 /media/WINDOWS ntfs ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks 0 0

[/B][/I]
I added fixed mounts to fstab:

[I][B]LABEL=Data    /media/fsData    ntfs    defaults        0    2
LABEL=WINDOWS    /media/fsWINDOWS ntfs    defaults        0    2
[/B][/I]
and now mtab looks like this:

[I]/dev/sda6 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
[B]/dev/sda3 /media/fsData ntfs ro 0 0
/dev/sda2 /media/fsWINDOWS ntfs ro 0 0
[/B]binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/jeremy/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=jeremy 0 0
[/I]
When I run the Ubuntu Live CD, everything is fine and the drives are writeable, and mtab looks like this:

[I]/cow / overlayfs rw 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
/dev/sr0 /cdrom iso9660 ro,noatime 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ubuntu 0 0
[B]/dev/sda3 /media/Data fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
/dev/sda2 /media/WINDOWS fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
[/B][/I]a few more possible hints: 

1: when I loaded gparted and looked at the partitions, it said there were errors on the WINDOWS drive and I should run chkdsk, which I did. (see above)

2: when I first noted the problem there were two folders (inaccessible) in media by the same names as the drives and the read-only mounts were being mounted as Drive_  - a definite change since I'd been writing scripts that run on files in these drives and they'd had no underscore then.


does anyone out there know all the configuration files relating to this?

I'm running 64bit Ubuntu 11.10 on a toshiba laptop with Intel i3 and 4Gb ram. I am on kernel 3.0.0.12, everything is basically vanilla as it came off the CD except for the software I've installed.

I hope someone out there can help me.

---

### Post by cybercity@localhost on 2012-04-16
according to your fstab conf your partitions are being mounted as read-only file system on boot... you have to manually edit your fstab configuration file carefully. go through this guide...

```
 http://opensuse.swerdna.org/susentfs.html 
```

---

### Post by Morbius1 on 2012-04-16
According to what he posted his fstab has the correct setting:
> I added fixed mounts to fstab:

[I][B]LABEL=Data    /media/fsData    ntfs    defaults        0    2
LABEL=WINDOWS    /media/fsWINDOWS ntfs    defaults        0    2
[/B][/I]Assuming of course those are the real partition labels and the two mountpoints actually exist. Btw I would change the last digits on both lines to "0" ( that's a zero ) instead of a "2".

You can always verify if the labels are right by looking at the output of the following command:
```
sudo blkid -c /dev/null
```If I had to hazard a guess to this the cause of this dilemma I would guess that somehow the following package was installed: **ntfsprogs**.

If you install ntfsprogs it will automatically remove the ntfs-3g driver. ntfs-3g is the thing that enables an ntfs partition to be writeable. So I would:

* Remove ntfsprogs
* Install ntfs-3g. 
* If any of these ntfs partitions are currently mounted unmount them.
* Run the following command to test for errors and mount the partitions:
```
sudo mount -a
```If it finds a problem "sudo mount -a" will output error messages so post them back here.

---

### Post by wildwood on 2012-04-16
Thanks morbius! it was indeed ntfsprogs, installed as an option with gparted (listed as "Tools for doing neat things with NTFS partitions in Linux). have put ntfs-3g in with synaptics and instant recovery, no need for static mounts (I had removed them in the process of winding back to get all the info in the original question) - fuse discovers and mounts dynamically as it used to. Thanks again!

---

### Post by Morbius1 on 2012-04-16
>  it was indeed ntfsprogs, installed as an option with gpartedI went into synaptics and it does list ntfsprogs as a "Suggest" under "Dependencies". Somebody didn't do their homework when they put together the package on this one.

---

### Post by AraiBob on 2012-04-23
Thanks for this valuable information. I had 3 ntfs internal drives, and the usb external drives all suddenly marked as 'read only'. Very annoying.

---

