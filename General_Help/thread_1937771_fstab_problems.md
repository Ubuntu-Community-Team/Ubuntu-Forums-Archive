---
title: "fstab problems"
date: 2012-03-08
forum: General Help
---

### Post by gclayton on 2012-03-08
Okay, here we go again. I'm having a time getting my filesystems to mount during the boot process. I can't reason out why my fstab gives an error on gid and uid when booting. I have no trouble mounting by hand and changing group and user after it's mounted, but would be nice to just log in and go. I will include my fstab here and the error message from syslog as well. If anybody can show me the error of my way I will be very thankful. The error log was generated after a used   mount -a to try the fstab again.
 
fstab

/dev/fd0                                   /media/floppy0           vfat  noauto                                  0  0  
UUID=89daeef3-ce69-48c4-ad74-0c484f2b892b  /                        ext4  defaults                                0  1  
UUID=8dab92f2-f345-409f-a617-8e912fdaf7d4  /srv/samba/share/stores  ext4  nomand,group,users,rw,gid=100,uid=1000  0  0  

[  239.465112] Bluetooth: RFCOMM socket layer initialized
[  239.465118] Bluetooth: RFCOMM ver 1.11
[  239.472359] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  239.472366] Bluetooth: BNEP filters: protocol multicast
[  239.833145] init: plymouth-stop pre-start process (1482) terminated with status 1
[  249.496009] eth0: no IPv6 routers present
[  394.086840] EXT4-fs (sda1): re-mounted. Opts: commit=0
[  693.021342] EXT4-fs (sdb1): Unrecognized mount option "gid=100" or missing value
[ 1661.447549] EXT4-fs (sdb1): Unrecognized mount option "uid=1000" or missing value

---

