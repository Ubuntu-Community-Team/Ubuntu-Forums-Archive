---
title: "Problem automounting external hard drive via fstab"
date: 2009-08-18
forum: General Help
---

### Post by delcypher on 2009-08-18
Hi there. I'm having problems getting an external USB hard drive to automount using the /etc/fstab file. Here's what it is currently.

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=e203b746-1eea-47e5-b407-c1c8e902d8d6 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=7904ee50-fe88-407b-a61b-6a30ff342512 /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=b992a0b0-aa99-45d0-b5a8-2f5f23da6930 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

#addition
UUID=7A362FCD362F88E9    /media/Data     ntfs-3g         defaults        0 0

```

The line after #addition is what I've added. If I run ```
sudo mount -a
``` then the file system is mounted fine. However when I boot up the computer, the USB drive mentioned in /etc/fstab is not mounted. I don't understand why this is happening. Does anyone have any suggestions or log files I could look at?

--Before I made the change to /etc/fstab. I could mount the drive through NAUTILUS (GNOME) just by clicking on it but now it says 

"Unprivileged user can not mount NTFS block devices using external FUSE library. Either mount volume as root, or rebuild NTFS-3G with integrated FUSE support and make it setuid root."

so I'm forced to go to the terminal and mount it as root.

---

### Post by cgb on 2009-08-18
Not entirely sure if this is the problem but for my usb drive I mount using the below code in fstab instead of UUID=.  

```
/dev/disk/by-uuid/0b4f64e1-e932-49e9-b983-d595fb386e62 /media/usbBackup	ext4	defaults	0	0
```

---

### Post by delcypher on 2009-08-18
Thanks but that didn't help. I still have the same problem.

---

