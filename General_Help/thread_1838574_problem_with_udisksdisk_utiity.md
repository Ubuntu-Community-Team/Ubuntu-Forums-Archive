---
title: "problem with udisks/disk utiity"
date: 2011-09-03
forum: General Help
---

### Post by moonpoppy on 2011-09-03
i was using a verbatim tuff and tiny usb drive earlier today. i tried to reformat it. and it failed and made havoc everywhere. it destroyed several other usb drives (every usb drive i used after the tuff and tiny was corrupted upon trying to reformat them. and it left a trace on an external hd and an external dvd burner. it even froze up the computer. i couldn't erase the internal hd until i mounted the dvd drive and then reinstalled ubuntu from there. but what's incredible to me is that the error from the previous installation persists in the new one. it seems it was passed on from the dvd drive. i have had that drive for years and been using 11.04 for 3 months and this is the first time i have experienced this generic /xd/sd/ms issue..

the bug may be in udisks. i am pretty much a newbie though. i could be wrong. 

to test my hypothesis, is there a way i can remove udisks and all its config files without breaking the desktop? in synaptic it seems you have to remove the core of the os to remove udisks, ie the desktop!

i tried killall udisks and udisks --dump and then logged out and that did nothing.

there is no external media attatched to my computer.

this is a desktop photo of disk utility (see attached photo - it's same computer - 2 diff sessions- same problem -it looks diff bc i just was redoing appearance)

```
udisks --dump
Showing information for /org/freedesktop/UDisks/devices/sdb
  native-path:                 /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/host4/target4:0:0/4:0:0:0/block/sdb
  device:                      8:16
  device-file:                 /dev/sdb
    presentation:              /dev/sdb
    by-path:                   /dev/disk/by-path/pci-0000:03:00.0-scsi-0:0:0:0
  detected at:                 Sat 03 Sep 2011 09:13:03 PM EDT
  system internal:             0
  removable:                   1
  has media:                   0
    detects change:            1
    detection by polling:      1
    detection inhibitable:     1
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  size:                        0
  block size:                  0
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  drive:
    vendor:                    Generic-
    model:                     xD/SD/M.S.
    revision:                  1.00
    serial:                    
    WWN:                       
    detachable:                0
    can spindown:              0
    rotational media:          Yes, unknown rate
    write-cache:               unknown
    ejectable:                 0
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     
      compat:                  flash_sd
    interface:                 scsi
    if speed:                  (unknown)
    ATA SMART:                 not available

``````
gvfs-mount -li
Drive(0): SecureDigital Drive
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  ids:
   unix-device: '/dev/sdb'
  themed icons:  [drive-removable-media-flash-sd]  [drive-removable-media-flash]  [drive-removable-media]  [drive-removable]  [drive]
  is_media_removable=1
  has_media=0
  is_media_check_automatic=1
  can_poll_for_media=1
  can_eject=0
  can_start=0
  can_stop=0
  start_stop_type=unknown

``````
sudo fdisk -l
[sudo] password for t: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001df80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30142   242113536   83  Linux
/dev/sda2           30142       30402     2082817    5  Extended
/dev/sda5           30142       30402     2082816   82  Linux swap / Solaris
-AOD257:~$ sudo blkid
/dev/sda1: UUID="670e5404-363a-4d79-b7a6-0f173c18d17d" TYPE="ext4" 
/dev/sda5: UUID="a5e0cc66-a74b-4876-92a0-641546cc4968" TYPE="swap" 

``````
 sudo cat /proc/self/mountinfo
[sudo] password for t: 
14 19 0:14 / /sys rw,nosuid,nodev,noexec,relatime - sysfs none rw
15 19 0:3 / /proc rw,nosuid,nodev,noexec,relatime - proc none rw
16 19 0:5 / /dev rw,relatime - devtmpfs none rw,size=1017608k,nr_inodes=214851,mode=755
17 16 0:11 / /dev/pts rw,nosuid,noexec,relatime - devpts none rw,gid=5,mode=620,ptmxmode=000
18 14 0:15 / /sys/fs/fuse/connections rw,relatime - fusectl fusectl rw
19 1 8:1 / / rw,relatime - ext4 /dev/disk/by-uuid/670e5404-363a-4d79-b7a6-0f173c18d17d rw,errors=remount-ro,barrier=1,data=ordered
21 14 0:6 / /sys/kernel/debug rw,relatime - debugfs none rw
22 14 0:10 / /sys/kernel/security rw,relatime - securityfs none rw
23 16 0:16 / /dev/shm rw,nosuid,nodev,relatime - tmpfs none rw
24 19 0:17 / /var/run rw,nosuid,relatime - tmpfs none rw,mode=755
25 19 0:18 / /var/lock rw,nosuid,nodev,noexec,relatime - tmpfs none rw
26 15 0:19 / /proc/sys/fs/binfmt_misc rw,nosuid,nodev,noexec,relatime - binfmt_misc binfmt_misc rw
28 19 0:20 / /home/t/.gvfs rw,nosuid,nodev,relatime - fuse.gvfs-fuse-daemon gvfs-fuse-daemon rw,user_id=1000,group_id=1000
```i have a list of virtual devices but i have no idea what it means. i can post upon request.

i hope someone can help.

---

### Post by elvis_ef on 2012-03-11
Similar problem:

> [http://ubuntuforums.org/showthread.php?p=11747087](http://ubuntuforums.org/showthread.php?p=11747087)

---

