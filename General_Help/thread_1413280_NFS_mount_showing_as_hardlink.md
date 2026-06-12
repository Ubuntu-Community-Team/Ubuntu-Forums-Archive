---
title: "NFS mount showing as hardlink?"
date: 2010-02-22
forum: General Help
---

### Post by myth1914 on 2010-02-22
I've recently found that I have direct paths to certain folders in my root directory.  For example:

/DVDs
/videos
/music

The actual path to these folders is something like:

/var/lib/mythtv/videos/DVDs
/var/lib/mythtv/videos
/var/lib/mythtv/music

The only correlation I've been able to make is that I'm exporting the same directories via NFS.

I have NOT used hardlinks for various reasons, but I would like to understand why these paths are showing directly under root?  I should note that the /DVDs does not show in an "ls -lh /"; however, /music and /videos shows as a directory (not a symlink)ls
 with me:me 777.  I know the 777 was me from a while back, but for the life of me, I can't figure out this behavior.

I've tried to look this up, but can't find anything related to what I'm seeing.  Any thoughts?

```
lrwxrwxrwx    1 root   root     33 2009-12-26 14:49 initrd.img.old -> boot/initrd.img-2.6.31-17-generic
-rw-r--r--    1 root   root    47K 2009-11-29 18:15 job_order_form_06-07a.doc
drwxr-xr-x   14 root   root    12K 2010-02-07 14:23 lib
drwxr-xr-x    7 root   root    12K 2010-01-11 06:03 lib32
lrwxrwxrwx    1 root   root      4 2008-11-21 18:14 lib64 -> /lib
drwx------    2 root   root    16K 2008-11-21 18:13 lost+found
drwxr-xr-x    4 root   root   4.0K 2010-02-21 19:52 media
drwxr-xr-x    2 root   root   4.0K 2008-06-13 14:40 mnt
[COLOR=Red]drwxrwsrwx 2132 me   me   1.1M 2010-02-21 22:05 music[/COLOR]
drwxr-xr-x    4 root   root   4.0K 2009-12-26 12:55 opt
dr-xr-xr-x  260 root   root      0 2010-02-21 19:52 proc
drwxr-xr-x   30 root   root   4.0K 2010-01-18 20:37 root
drwxr-xr-x    2 root   root   4.0K 2010-02-07 14:23 sbin
drwxr-xr-x    2 root   root   4.0K 2009-03-06 10:16 selinux
-rw-------    1 root   root    32K 2009-12-26 13:42 sqlPLPodA
drwxr-xr-x    3 root   root   4.0K 2009-12-26 14:50 srv
drwxr-xr-x   13 root   root      0 2010-02-21 19:52 sys
drwxrwxrwt   19 root   root    12K 2010-02-22 06:49 tmp
drwxr-xr-x   11 root   root   4.0K 2009-12-26 14:36 usr
drwxr-xr-x   17 root   root   4.0K 2008-11-23 19:40 var
[COLOR=Red]drwxrwsr-x   16 mythtv mythtv 4.0K 2010-02-22 06:30 videos[/COLOR]
<snip>
me@Xeon:/$ ls
bin    dev   export  initrd.img                 lib    lost+found  [COLOR=Red]music[/COLOR]  root     sqlPLPodA  tmp  [COLOR=Red]videos[/COLOR]       webmin-setup.out
boot   [COLOR=Red]DVDs[/COLOR]  home    initrd.img.old             lib32  media       opt    sbin     srv        usr  vmlinuz      zm-1.22.3.dump
cdrom  etc   initrd  job_order_form_06-07a.doc  lib64  mnt         proc   selinux  sys        var  vmlinuz.old

```

---

### Post by maweki on 2010-02-22
could you please post your /etc/fstab

thanks

---

### Post by myth1914 on 2010-02-22
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=75a3e99d-e5b9-42f1-9e5f-70cca14d13bf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a6686a76-936e-4f37-855e-fef396055c82 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1  /var/lib/mythtv/recordings  ext3  suid,dev,exec,relatime  0  0
/var/lib/mythtv/music  /music  bind  bind  0
/dev/sdc1  /var/lib/mythtv/videos  ext3  suid,dev,exec,relatime  0  0
/var/lib/mythtv/videos  /videos  bind  bind  0
/var/lib/mythtv/videos/DVDs  /DVDs  bind  bind  0

```ok, so after reading your request, I got a big DUH for some of this, but I still don't see the correlation to the /DVDs showing in ls, but not in ls -l...

---

### Post by maweki on 2010-02-22
please remember: a mount is not a symlink.

please do an "ls -al" and check the results again.

Edit: "boot" and "home" are also missing. Maybe there was just not enough screen size to print "DVDs" in the list. You could use shift and page-up (I think so) to scroll up in the terminal or send your input through a pipe through less or more.

> ls -al / | less

---

### Post by myth1914 on 2010-02-22
> **maweki said:**
> please remember: a mount is not a symlink.

please do an "ls -al" and check the results again.

Edit: "boot" and "home" are also missing. Maybe there was just not enough screen size to print "DVDs" in the list. You could use shift and page-up (I think so) to scroll up in the terminal or send your input through a pipe through less or more.


And there it is!  I think I just needed the symlink in my brain!  Thanks for the help!

---

