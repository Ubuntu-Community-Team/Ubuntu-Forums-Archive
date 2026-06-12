---
title: "drive to mount on /home/ross/flash not ready yet press s to skip ..."
date: 2010-06-11
forum: General Help
---

### Post by josephellengar on 2010-06-11
I have a flash drive that I put in my fstab so that it will automatically mount on the same folder every time but I do not always have it to mount on boot.  I just upgraded to 10.04 and now it will not turn the computer on unless I press "s" or "m" when it is ready to mount this drive.  Is there a way that I can tell it not to mount this drive on boot?  My fstab reads as follows:

```

# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0

# root filesystem
UUID=098c0e33-2ea8-420a-a7c9-2bcdc9011118 / ext4 errors=remount-ro 0 1

# swap file
UUID=0de4ba0c-7406-4974-a25b-a1d10f68be39 none swap sw 0 0

#storage
/dev/sdb1 /home/ross/storage ntfs-3g auto,user,uid=1000,gid=100,dmask=027,fmask=137,utf8 0 0

#flash drive
/dev/sdc1 /home/ross/flash vfat iocharset=utf8,umask=000,user 0 0

```

---

