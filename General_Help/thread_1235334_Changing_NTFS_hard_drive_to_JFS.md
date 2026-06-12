---
title: "Changing NTFS hard drive to JFS"
date: 2009-08-09
forum: General Help
---

### Post by pozzitron on 2009-08-09
I had an ntfs drive (/dev/sdb1)  that held all my media. I moved my media to another hdd and formated the hdd using partition editor to jfs. When I rebooted I did not see the icon on my desktop like before but i could still see the hdd under the "Places" menu. I can access the hdd by authenticating, but i am not able to read/write files in there. I figure I need to change something in fstab, but i am not sure to what.

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# / was on /dev/sda3 during installation
UUID=0b01b437-2ca7-4e40-85f6-6000bdb9ac00 /     jfs     relatime,errors=remount-ro 0       1

/dev/sda5 /home jfs nodev,nosuid 0 2

[COLOR=Red]# /media/storage1 was on /dev/sdb1 during installation
UUID=86746FFD746FEDFD /media/storage1 ntfs    defaults,nls=utf8,umask=007,gid=46 0       1[/COLOR]

# /media/storage2 was on /dev/sdc1 during installation
UUID=8078C55678C54B9A /media/storage2 ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

# swap was on /dev/sda1 during installation
UUID=4b5a039c-a18b-424d-aaee-5325a88278c8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

I would greatly appreciate any help or suggestions.

---

### Post by Bucky Ball on 2009-08-09
Post result of:

sudo blkid

---

### Post by pozzitron on 2009-08-09
> **Bucky Ball said:**
> Post result of:

sudo blkid
/dev/sda1: TYPE="swap" UUID="4b5a039c-a18b-424d-aaee-5325a88278c8" 
/dev/sda3: UUID="0b01b437-2ca7-4e40-85f6-6000bdb9ac00" TYPE="jfs" 
/dev/sda5: UUID="b9548f9e-fd27-40cd-b769-193ec4902d63" TYPE="jfs" 
/dev/sdb1: UUID="f23806ed-86df-413e-bcde-f489b709f007" TYPE="jfs" 
/dev/sdc1: UUID="8078C55678C54B9A" LABEL="Video Vault 1TB" TYPE="ntfs"

---

### Post by Bucky Ball on 2009-08-09
Yea, not sure what has happened there but things have changed radically. 

I would perhaps start by checking /media and making sure all the correct mount point are there. If not, you can make them with:
```

sudo mkdir /media/mount_point_name
```... where  'mount_point_name' is your mount point.

Now you need to match up the correct UUIDs in 'sudo blkid' with your mount points in fstab, if you follow me.

Are your partitions all still as they were on the desktop except the one you have just formatted or they have all changed around and need to be manually mounted?

---

### Post by pozzitron on 2009-08-09
I checked /media and both mount points are there.The second hdd is there working the way it was before, shortcut on desktop and all.  When I match the UUIDs on fstab with the ones from 'sudo blkid' for the hdd in question would I have to change the NTFS to JFS.. What about the rest of the line?

---

