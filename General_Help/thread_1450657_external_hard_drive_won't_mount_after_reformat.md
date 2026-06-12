---
title: "external hard drive won't mount after reformat"
date: 2010-04-09
forum: General Help
---

### Post by rmedved on 2010-04-09
I recently reformatted my external hard drive. Somewhere along the way I think my fstab got messed up because now my hard drive won't mount. Instead I get the following error:

Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

If I mount it through Gparted, it mounts just fine.

my fstab currently looks like this: 

# system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda4
UUID=3bdd4555-0066-4b39-8129-1604516cd406  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda3
UUID=20392bfe-e56c-4388-8beb-5dcc706c9478  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdb1                                  /media/sdb1    vfat         owner,users,user            0  0  


any help would be awesome,
robbie

---

### Post by moetunes on 2010-04-09
I guess the disk is  /dev/sdb1 - did you reformat it as fat 16 or 32?

---

### Post by rmedved on 2010-04-09
Ntfs

---

### Post by coffeecat on 2010-04-09
> **rmedved said:**
> Ntfs

I presume you have a particular reason for mounting your external drive with a line in fstab? If you don't have a mount line in fstab, it will be automounted when you plug it in and switch it on. It'll be automounted for you during bootup if you have it switched on before you boot up too. So the easiest option would be simply to remove this line from /etc/fstab:

> **rmedved said:**
> /dev/sdb1                                  /media/sdb1    vfat         owner,users,user            0  0

... and let udev do it for you.

But if you do have a reason for using fstab, then change that line to:

```
/dev/sdb1     /media/sdb1     ntfs     defaults    0  0
```

---

