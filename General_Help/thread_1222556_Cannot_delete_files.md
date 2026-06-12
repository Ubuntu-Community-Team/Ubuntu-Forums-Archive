---
title: "Cannot delete files"
date: 2009-07-25
forum: General Help
---

### Post by jhapk on 2009-07-25
Hi,

I have mounted my partitions using the following fstab file
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=b451f4ea-89b4-46a7-9c2e-f14254b59055 /               ext3    relatime,errors=remount-ro 0       1
/dev/sda2       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1       /chile    auto    defaults,user        0       0                 
/dev/sda3       /zambia   auto    defaults,user        0       0
/dev/sda6       /mongolia auto    defaults,user        0       0
/dev/sda7       /pitcairn auto    defaults,user        0       0
/dev/sda8       /moldova  auto    defaults,user        0       0

```

I am not able to delete or write anything on these folders without the
root permission. I tried 

```
$sudo chmod 777 *

```
but even then it doesn't seem to change the permissions which always shows

```
-rwxr-xr-x 1 root root 0 2009-06-04 15:40 File
```

any clues?
Thanks

---

### Post by mikewhatever on 2009-07-25
Be careful with chmod 777. Issued without a target, it chmods the current directory, most probably your home folder, a bad idea in multiuser environment. If you really want to chmod a mount point, try chmod 777 /chile, but that shouldn't be needed in most cases. Instead, give yourself or a group the ownership of these partitions with chown.
chown -R jhapk /chile

I'd strongly suggest reading through the following man entries:
man chown
man chmod

---

### Post by SuperSonic4 on 2009-07-25
I'd also chown the directory in question to you ```
chown -Rv group:user /chile
```

If you need to be root preface the command with sudo or use sudo !! to run the last command as root

---

