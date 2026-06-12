---
title: "Devices not automounting"
date: 2004-10-19
forum: General Help
---

### Post by paul.hendrick on 2004-10-19
Hi
Im using ubuntu, and i've upgraded to the latest packages.
my current user account was added by the user-admin tool, and i think it's buggy as it doesnt create a home directory, etc, so i'm not sure if my /home permissions are correct for automounting to work.

if i run gnome-volume-manager from the terminal, and insert a cdrom, there's no output whatsoever. 

any ideas about this?

---

### Post by im_ka on 2004-10-19
could you copy/paste your /etc/fstab file?

---

### Post by paul.hendrick on 2004-10-19
# /etc/fstab: static file system information.
#
# &lt;file system&gt; &lt;mount point&gt;   &lt;type&gt;  &lt;options&gt;       &lt;dump&gt;  &lt;pass&gt;
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /boot           ext3    defaults        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hda5       /home           ext3    rw,defaults     0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /win_xp         ntfs    auto,users,umask=0      0       0

---

### Post by im_ka on 2004-10-19
hmm... looks like mine.

go to computer/desktop-preferences/removable devices and see if the box automaticaly open removable devices (or something like that, my desktop is set to german)

this is how my fstab line for my /home partition looks like (created upon install):

```
/dev/hda2       /home           ext3    defaults        0       2
```

---

