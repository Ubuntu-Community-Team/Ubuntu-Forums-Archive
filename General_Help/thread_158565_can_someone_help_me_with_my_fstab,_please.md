---
title: "can someone help me with my fstab, please?"
date: 2006-04-11
forum: General Help
---

### Post by ice60 on 2006-04-11
hi i just had a look at my fstab and it looks like this

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/hda5       /media/windows2 ntfs    umask=0222

/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0


a while ago i was going to make a livecd but i didn't have enough HDD space to re/compile it. is that what all the stuff below is?
```
/tmp/app/x/image /tmp/app/x cramfs,iso9660 user,noauto,ro,loop,exec 0 0
```

how do i clean all of the iso stuff up :confused: thanks.

---

### Post by Monster_user on 2006-04-11
That is EXACTLY what that is. Copy that stuff out, and run '**gksu gedit /etc/fstab**' to edit it out.

All you have to do, is delete the entries. I would check to see if there is anything in your '/tmp/#' folders.

---

### Post by ice60 on 2006-04-11
thanks, Monster_user. the tmp directory looks OK so i'll just edit out the iso stuff, thanks for the help :)

---

