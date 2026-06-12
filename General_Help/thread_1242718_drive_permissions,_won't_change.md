---
title: "drive permissions, won't change"
date: 2009-08-17
forum: General Help
---

### Post by Support the 2nd on 2009-08-17
I cannot get my fat32 partition to change permission.  It is set at root and I when I select my user name, it says it cannot change it, "Could not change, operation not permitted".

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# / was on /dev/sdb6 during installation
UUID=fd820df4-d03d-446e-8e0e-9f82105582b1  /               ext3         relatime,errors=remount-ro  0  1  
# swap was on /dev/sdb5 during installation
UUID=c03b433d-0fe8-4a98-87af-c999099bf053  none            swap         sw                          0  0  
/dev/scd1                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sda1                                  /media/sda1     ntfs         nls=iso8859-1,ro,umask=000  0  0  
/dev/sdb3                                  /media/subway   vfat         defaults                    0  0  

```

---

### Post by credobyte on 2009-08-17
FAT32 doesn't support file permissions. You can try to mount it with root privileges:
```
sudo mount /dev/sdb3 /media/subway
```

---

### Post by Support the 2nd on 2009-08-17
> **credobyte said:**
> FAT32 doesn't support file permissions. You can try to mount it with root privileges:
```
sudo mount /dev/sdb3 /media/subway
```

I think I set it to auto mount with psydm.  Can I make it auto mount with root?

---

### Post by michy99 on 2009-08-17
You need to set the permissions at the time it is mounted. Change the line in fstab to read:```
/dev/sdb3                   /media/subway   vfat  utf8,umask=007,uid=1000        0  0
```

---

### Post by Support the 2nd on 2009-08-17
That worked.  thanks.

couple questions....

I took a risk as I couldn't find the command to backup fstab.  I read to use -B, but it didn't tell me the whole command.  I am not very good at my command lines.


Also, so I learn something rather than just copy/paste...

[INDENT]**uid=1000**
*is my user id and the 1000 is what ubuntu sees for this specific one?  Is there a place I can go to find those in the event of multiple users?

**umask=007**
*whats the difference between umask and dmask?  Is there a place I can find what 007 is verses another number?
[/INDENT]

---

