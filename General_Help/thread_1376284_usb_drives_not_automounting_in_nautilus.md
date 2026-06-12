---
title: "usb drives not automounting in nautilus"
date: 2010-01-09
forum: General Help
---

### Post by cnschulz on 2010-01-09
Howdy,

Stumped.

I can manually mount my iPod shuffle and USB key however they wont auto mount.

I cant remember when this stopped but i will admit i did move my install to a new disk. Perhaps there is a permission problem somewhere? the media folder my be incorrect?

drwxr-xr-x  18 root root  4096 2010-01-09 16:34 media

The devices are listed correctly in lsusb:
Bus 001 Device 008: ID 05ac:1301 Apple, Inc. iPod Shuffle 2.Gen

and dmesg | tail
[ 2233.640852] sd 4:0:0:0: [sdb] Write Protect is off
[ 2233.640858] sd 4:0:0:0: [sdb] Mode Sense: 64 00 00 08
[ 2233.640863] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2233.643417] sd 4:0:0:0: [sdb] 991232 2048-byte hardware sectors: (2.03 GB/1.89 GiB)
[ 2233.643911] sd 4:0:0:0: [sdb] Write Protect is off
[ 2233.643917] sd 4:0:0:0: [sdb] Mode Sense: 64 00 00 08
[ 2233.643922] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2233.643929]  sdb:
[ 2233.647912] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 2233.648468] sd 4:0:0:0: Attached scsi generic sg2 type 0

any ideas how i can get automount to work again?

c.

---

### Post by Leppie on 2010-01-09
check if you are in the fuse group, issue this command in a terminal:
```
cat /etc/group | grep fuse
```
if your username is not listed, add yourself to the group:
```
sudo useradd <username> fuse
```

also check that there's ***no*** entries in fstab for these devices.

---

### Post by cnschulz on 2010-01-15
sorry i took so long to reply...

im in that group.

btw ive just realised this happens with cd's too. if i put a cd in it will spin up then do nothing. if i issue 'mount /media/cdrom' it moints an operates normally.

bizarre.

---

### Post by Leppie on 2010-01-15
could you post your fstab?

---

### Post by cnschulz on 2010-01-16
> **Leppie said:**
> could you post your fstab?

That was it. Thanks folks. When i was fooling around with moving my ubuntu install i pasted in a uuid on the wrong side of the comment marker!

its strange that everything else worked tho! only auto mount stopped working.

see line 2 for error.

many many thanks.

# /etc/fstab: static file system information.
52366e93-4b9c-4f38-97df-fbf799115ef6#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=b05c710b-96f5-4259-adb8-44e96d6422ce /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=a788ef63-1c37-48ab-b347-18dd962e88a7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
UUID=c5c66d48-9496-4bd4-b204-c603dbb4dd8d 	/home	ext3	defaults,errors=remount-ro 0 1
# 
#/dev/sda5: UUID="" SEC_TYPE="ext2" TYPE="ext3" 
#/dev/sda6: TYPE="swap" UUID="a95616ee-23c4-4996-859a-eec8d0978d18" 
###/dev/sda7: UUID="b05c710b-96f5-4259-adb8-44e96d6422ce" TYPE="ext3" 
#/dev/sda8: TYPE="swap" UUID="a788ef63-1c37-48ab-b347-18dd962e88a7"
#
#
//192.168.1.3/audio /media/audio cifs username=xxxxx,password=xxxxx,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.3/video /media/video cifs username=xxxxx,password=xxxxx,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.3/photo /media/photo cifs username=xxxxx,password=xxxxx,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.3/download /media/download cifs username=xxxxx,password=xxxxx,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

---

