---
title: "cd and floppy drives won't mount"
date: 2010-09-02
forum: General Help
---

### Post by jedson3 on 2010-09-02
The basic problem is that after installing a brothers MFC-498CW printer/scanner I can't mount any of my non-usb disk drives (floppy, DVD or CD).  Had a hint there was a problem when I kept getting a message that there was a mounting problem when I would boot up in the morning. But it offered the option of hitting “S” and bypassing the mounting. My file system would mount when I did this. But then I found the other drives would not. Then this morning the file system itself would not mount. I tried it in “recovery mode” and received the message that “mount point /proc/bus/usb does not exist. Mountall: filesystem could not be mounted: /pros/bus/usb. Fsck from util-linux-ng 2.17.2.” whatever all that means. But it would seem that in enabling the brothers printer to mount I unhinged something that lets the drives to mount. 

Any help will be appreciated

Jedson

---

### Post by dcstar on 2010-09-02
> **jedson3 said:**
> The basic problem is that after installing a brothers MFC-498CW printer/scanner I can't mount any of my non-usb disk drives (floppy, DVD or CD).  Had a hint there was a problem when I kept getting a message that there was a mounting problem when I would boot up in the morning. But it offered the option of hitting “S” and bypassing the mounting. My file system would mount when I did this. But then I found the other drives would not. Then this morning the file system itself would not mount. I tried it in “recovery mode” and received the message that “mount point /proc/bus/usb does not exist. Mountall: filesystem could not be mounted: /pros/bus/usb. Fsck from util-linux-ng 2.17.2.” whatever all that means. But it would seem that in enabling the brothers printer to mount I unhinged something that lets the drives to mount. 

Any help will be appreciated

Jedson

If there is now a usbfs entry in /etc/fstab then it breaks 10.04, comment it out.

---

### Post by jedson3 on 2010-09-02
OK. Here is what my fstab file looks like now. You can see what I did on the bottom line. 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=6a16986d-c02e-4a1b-b181-bc3718f7c06c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=18cd301a-d969-445d-a03c-694ca7a2bd02 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

none /proc/bus/usb /* usbdevfs */ auto,devmode=0666 0 0


Now my DVD driver works again. But the 3.5 floopy still does not. On Brothers, it will still print things from my computer, but the scanner no longer works. Seems like a matter of getting the fox, the grain and the hen all across the river.

Jim

---

