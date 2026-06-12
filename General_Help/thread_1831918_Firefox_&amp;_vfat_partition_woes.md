---
title: "Firefox &amp; vfat partition woes"
date: 2011-08-24
forum: General Help
---

### Post by onebir on 2011-08-24
I'm trying to get a video download plugin for Firefox (Ant Video) to write into a vfat partition where there's more space. I keep getting the message "You can not read or write files in this folder."

Initially, the permissions for the folder were weird. I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=526903](http://ubuntuforums.org/showthread.php?t=526903) 

And edited /etc/fstab to this:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=b1e6a62a-ffba-4a34-a7dd-9b3cfa169095 /               ext4    errors=remount-ro 0       1
# /intldata was on /dev/sda7 during installation
#UUID=38CC-D54A  /intldata       vfat    utf8,umask=007,gid=46 0       1
**UUID=38CC-D54A  /intldata       vfat    utf8,umask=007,gid=1000,uid=1000 0 1**
# swap was on /dev/sda5 during installation
UUID=f5cc3678-13aa-4d1f-8371-087147891455 none            swap    sw              0       0
```The bold line is the one I changed; the commented-out one above is what was there before.

This has changed owner and group :

```
ls -lh | less
...
drwxrwx---  16 onebir onebir  32K 1970-01-01 02:00 intldata
...
```Since I'm logging in as onebir, I thought that would allow Firefox to access the folder.  But apparently not... What have I missed?

---

### Post by lovinglinux on 2011-08-24
You should look into AppArmor profile. It is probably preventing Firefox from saving on the partition.

On a side note, [check this thread]("http://ubuntuforums.org/showthread.php?t=1823763") about Ant Video.

---

