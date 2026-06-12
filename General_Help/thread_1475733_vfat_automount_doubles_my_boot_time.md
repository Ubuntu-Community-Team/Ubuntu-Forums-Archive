---
title: "vfat automount doubles my boot time"
date: 2010-05-07
forum: General Help
---

### Post by micheledm on 2010-05-07
Hi guys... I just discovered that automounting a fat32 partition (which i keep for exchanging file between Ubuntu & Win) slows down my boot time, from around 25secs to 1 minute. It does not behave in the same way for a ntfs partition (the vista partition itself).

Here it is my fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0

# / was on /dev/sda3 during installation
UUID=6b0de3ef-fea6-4be4-b60e-1926db6aacaf /               ext4    errors=remount-ro 0       1

#/media/data was on /dev/sda5 during installation
[B]UUID=01AF-17F4  /media/data     vfat    utf8,umask=007,gid=46 0       1
[/B]
# /media/win-vista was on /dev/sda1 during installation
UUID=14D045BDD045A5B8 /media/win-vista ntfs    defaults,nls=utf8,umask=007,gid=46 0       0

# swap was on /dev/sda6 during installation
UUID=c7c69976-27e9-49c0-aee8-17cb45bc63c0 none            swap    sw              0       0

UUID=343ee528-a5d8-434c-ad87-ed8ce2eec613 /home ext4 defaults,user_xattr 0 2
```

Any idea?

---

### Post by ACMiller on 2010-05-07
Hey, so if you change the last 1 to a 0, then the vfat partition won't be scanned for errors everytime your computer boots. Fortunately that's not your root partition, so should there be any errors on it that aren't picked up now on booting, they won't affect you too much.

Thus, the line should look like this:
UUID=01AF-17F4  /media/data     vfat    utf8,umask=007,gid=46 0       0

---

### Post by micheledm on 2010-05-07
25.23 secs, great boot time! Thnak you!

---

### Post by ACMiller on 2010-05-07
Great, glad that helped!

---

