---
title: "Cannot play dvd's"
date: 2009-11-27
forum: General Help
---

### Post by wack8282 on 2009-11-27
I can no longer play DVD's on Ubuntu.
I get the following message: "cannot mount volume:
invalid mount option when attempting to mount the volume 'OFFICE_SPACE'.
    *Office space is obviously the DVD I'm trying but I get the same for any, including DVD's I've burned on Ubuntu, that work on my dvd player

My FSTAB looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc    /proc    proc    defaults    0    0
# /dev/sda1
UUID=6c814527-5db0-4129-b3bc-f41a16213147    /    ext3    relatime,errors=remount-ro    0    1    # /dev/sda1
# /dev/sda3
UUID=5aea32d9-f557-461a-958a-011fe718ac27    /home    ext3    relatime    0    2    # /dev/sda3
# /dev/sda2
UUID=3d13dcef-1b8c-41d9-bada-a585b4022a2d    none    swap    sw    0    0    # /dev/sda2
/dev/scd0    /media/cdrom0    udf,iso9660    user,Auto,exec,utf8    0    0

---

