---
title: "external USB drive weirdness"
date: 2009-12-30
forum: General Help
---

### Post by ray field on 2009-12-30
as of this morning, suddenly I'm having a hard time accessing the SimpleDrive 1tb external HD on Jaunty. formerly, I could plug it in: a Nautilus window would open with its contents, and I had all the access I wanted.

today, the first time I plugged it in, I got, "You don't have the necessary privileges to mount this drive."  

tried shutting down & rebooting.  the SimpleDrive shows up in Nautilus, but when I try clicking on it, I get

```
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending
```


tried using psdym to see if I could get a clue there -- it lists /sdb1, which I don't recognize.  I have an SD card reader which I use as a sort of on-the-fly backup which is always plugged in -- (I am used to getting a "Disk 1 is not ready, press any key to continue" message from the BIOS on bootup -- which is listed as /sdc1.  

here is my fstab if it's of any use:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc            proc         defaults                    0  0  
# / was on /dev/sda18 during installation
UUID=08478e3e-49bd-4991-9a60-bfd7d405e948  /                ext3         relatime,errors=remount-ro  0  1  
# /boot was on /dev/sda17 during installation
UUID=1b24c94e-3744-424b-b840-58c4aee3f0fc  /boot            ext3         relatime                    0  2  
# /home was on /dev/sda19 during installation
UUID=553b909b-6b9b-49d2-a495-362e9a7c0364  /home            ext3         relatime                    0  2  
# swap was on /dev/sda16 during installation
UUID=661f8d6d-ba39-48b5-b0fb-65eb0b3a160b  none             swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0    udf,iso9660  user,noauto,exec,utf8       0  0  
# /dev/sda5                                  /dosdisc        hpfs         

# /dev/sda5                                  /media/dosdisk_  hpfs        users,user,owner            0  0  
# /dev/sda5                                    /media/dosdisk_  ntfs-3g     utf8,umask=007,uid=1000,gid=46 0 0
/dev/sda5                                  /media/dosdisk_  hpfs         umask=007,uid=1000,gid=46   0  0  
/dev/sdc1                                  /media/SD_BAK    vfat         umask=007,uid=1000,gid=46   0  0  
/dev/sdb1                                  /media/sdb1      vfat         defaults                    0  0  
```

---

