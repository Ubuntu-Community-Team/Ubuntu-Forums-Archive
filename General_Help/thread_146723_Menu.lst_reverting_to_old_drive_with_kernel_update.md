---
title: "Menu.lst reverting to old drive with kernel update"
date: 2006-03-18
forum: General Help
---

### Post by skirkpatrick on 2006-03-18
My daughter has a dual-boot machine and after reading a forum thread about  using the "map" command in menu.lst to make Windows think it's the primary drive when it isn't so that it's updates won't screw up the MBR on the primary Ubuntu drive, I swapped her machine around and it's working fine.  The Ubuntu drive was originally hdb and Ubuntu was installed that way.  Now it is hba and I've modified menu.lst to reflect this.  However, everytime I update her kernel so that menu.lst gets modified to reflect the new kernel, it wants to put Ubuntu back at hdb.  Where is the config file that I can change so that Ubuntu thinks it is now on hda instead of hdb so that kernel updates don't mess up menu.lst?

---

### Post by lha on 2006-03-19
[QUOTE=skirkpatrick]My daughter has a dual-boot machine and after reading a forum thread about  using the "map" command in menu.lst to make Windows think it's the primary drive when it isn't so that it's updates won't screw up the MBR on the primary Ubuntu drive, I swapped her machine around and it's working fine.  The Ubuntu drive was originally hdb and Ubuntu was installed that way.  Now it is hba and I've modified menu.lst to reflect this.  However, everytime I update her kernel so that menu.lst gets modified to reflect the new kernel, it wants to put Ubuntu back at hdb.  Where is the config file that I can change so that Ubuntu thinks it is now on hda instead of hdb so that kernel updates don't mess up menu.lst?[/QUOTE]

The file you are looking for is /boot/grub/menu.lst. :) Find a section like this:
```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

```
and change lines
```
# kopt=root=/dev/hdb2 ro
``` and
```
# groot=(hd1,1)
``` to correct values. They seem to be commented out, but don't let it fool you. Those option (along with some others) are used to recreate menu.lst when you install a new kernel.

---

### Post by skirkpatrick on 2006-03-24
Thank you very much!  I never know when the comments are real comments and when they aren't :)

---

