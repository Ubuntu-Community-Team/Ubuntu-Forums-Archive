---
title: "Xen install error"
date: 2012-03-27
forum: General Help
---

### Post by forSC1ENCE on 2012-03-27
Im trying to install Xen, following the guide located here:
[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

Running ubuntu 11.10
kernel 3.0.0-16 generic
GNOME 3.2.1
64-bit system

when i get to 

sudo make xen

it seems to work fine until
 

grant_table.c: In function ‘__gnttab_unmap_common’:
grant_table.c:733:22: error: variable ‘old_pin’ set but not used [-Werror=unused-but-set-variable]
cc1: all warnings being treated as errors

make[4]: *** [grant_table.o] Error 1
make[4]: Leaving directory `/usr/src/xen-4.0.1/xen/common'
make[3]: *** [/usr/src/xen-4.0.1/xen/common/built_in.o] Error 2
make[3]: Leaving directory `/usr/src/xen-4.0.1/xen/arch/x86'
make[2]: *** [/usr/src/xen-4.0.1/xen/xen] Error 2
make[2]: Leaving directory `/usr/src/xen-4.0.1/xen'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/usr/src/xen-4.0.1/xen'
make: *** [install-xen] Error 2

Ive searched around the forums, but have been unable to find an answer. Thanks for helping a Linux newbie!

---

