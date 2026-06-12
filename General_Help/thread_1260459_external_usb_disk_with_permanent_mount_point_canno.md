---
title: "external usb disk with permanent mount point: cannot mount volume"
date: 2009-09-07
forum: General Help
---

### Post by chinaski on 2009-09-07
I have one 1TB external usb drive with 4 partition on it (2 NTFS + 2 FAT32) which are all data partition shared in my LAN

I set a permanent mount point in /media/something for the NTFS partition as those are the ones actually shared over the LAN, the problem is every time I reboot Ubuntu, I need to mount NTFS partition with sudo mount -a otherwise I get the following message:

Cannot mount volume. You are not privileged to mount this volume

I chown and chmod them but I still get this error

this is my fstab (bold highlights NTFS partition):

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
UUID=f085e7bc-42b3-49ae-8f85-da6bfbe91f88 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6ab9535e-35d9-4b3d-9693-0c9a825d39ae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# monto il secondo disco interno
/dev/sdb1    /storage    ext3    defaults    0    0

# monto USB per VirtualBox
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

# monto hd usb 1tb
# monto partizione personale 
**/dev/disk/by-id/usb-TrekStor_DS_maxi_g.u_00E75119-0:0-part2 /media/pers_usb1tb ntfs-3g defaults,locale=en_US.UTF-8 0 0**
# monto partizione acp
**/dev/disk/by-id/usb-TrekStor_DS_maxi_g.u_00E75119-0:0-part1 /media/acp_usb1tb ntfs-3g defaults,locale=en_US.UTF-8 0 0**
```I searched the forum and googled, but all I can get is automount without permanent mount point or permanent mount point with no automount

there must be a way to get both :P

---

### Post by chinaski on 2009-09-15
up

---

### Post by chinaski on 2009-09-20
hey people don't mean to sound rude or something, but **if** an automount on an external usb disk with permanent mount point is such an issue, let's stop yelling about how ready it's Linux for the desktop because it isn't

**if**... ;)

---

