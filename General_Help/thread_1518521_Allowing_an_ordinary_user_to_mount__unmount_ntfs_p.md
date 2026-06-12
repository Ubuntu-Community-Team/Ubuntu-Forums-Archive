---
title: "Allowing an ordinary user to mount / unmount ntfs partition"
date: 2010-06-26
forum: General Help
---

### Post by shiningoak on 2010-06-26
Hi,

Is there a way to allow ordinary users to mount / unmount an ntfs partition?

I don't want it to be mounted automatically - I can do that. I want it to be mount / unmountable by ordinary users (possibly in a particular group).

I'm using Ubuntu 10.04.

Thanks.

---

### Post by dabl on 2010-06-26
From ```
man mount
```


>  The non-superuser mounts.
              Normally, only the superuser can mount  filesystems.   However,  when  fstab
              contains the user option on a line, anybody can mount the corresponding sys&#8208;
              tem.

              Thus, given a line

                     /dev/cdrom  /cd  iso9660  ro,user,noauto,unhide

              any user can mount the iso9660 filesystem found on his CDROM using the  com&#8208;
              mand

                     mount /dev/cdrom

              or

                     mount /cd

              For more details, see fstab(5).  Only the user that mounted a filesystem can
              unmount it again.  If any user should be able to  unmount,  then  use  users
              instead  of user in the fstab line.  The owner option is similar to the user
              option, with the restriction that the user must be the owner of the  special
              file.  This  may be useful e.g. for /dev/fd if a login script makes the con&#8208;
              sole user owner of this device.  The  group  option  is  similar,  with  the
              restriction that the user must be member of the group of the special file.

---

