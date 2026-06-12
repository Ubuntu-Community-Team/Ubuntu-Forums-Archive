---
title: "Using filesystem extended attributes"
date: 2010-09-03
forum: General Help
---

### Post by jjmerelo on 2010-09-03
Hi,
I have been trying to set filesystem extended attributes on my Ubuntu 10.04 box. 
Kernel configuration seems to be OK:
> cat /boot/config-2.6.32-24-generic | grep EXT4
CONFIG_EXT4_FS=y
CONFIG_EXT4_FS_XATTR=y
CONFIG_EXT4_FS_POSIX_ACL=y
CONFIG_EXT4_FS_SECURITY=y
-
Then, mount options are as follows:
UUID=1d2d8088-137d-4127-a4c6-3a009bd83ca6 /               ext4    relatime,user_xattr,errors=remount-ro 0       1
-
But this happens:
> touch kk
[jmerelo@raj]  {09/03/10 09:09}  (/tmp)
> setfattr -n foo -v bar kk
setfattr: kk: Operación no soportada
--
OK, operation not supported. How can I check that user_xattr are enabled, and is there anything else I need to do?

---

