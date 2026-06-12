---
title: "Device permission problems"
date: 2006-02-07
forum: General Help
---

### Post by overcl0k3r78 on 2006-02-07
hello,
   I have been using linux on and off for about a year, but now on and I might add, on for good :mrgreen: (tired of Microsoft's shinanigans) but anyway, In Ubunu 5.10, I cant seem to alter device permissions for my floppy drive, USB drive, etc.  I tried the sudo chmod with various commands, however nothing worked.  I tried su and chmod.  didn't work......I can't seem to find ANY way to change the read/write permissions of my USB and Floppy drives.  oh, and I even tried the whole    sudo chmod /proc/  with the individual bus #'s and such.   any help or ideas would be appreciated.

---

### Post by nanotube on 2006-02-07
your usb and floppy drives are formatted with fat32. fat32 does not support unix-style permissions. the only way to change permissions is at mount-time, by giving it a drive-wide umask (so that all files on the drive have the same permissions).
see this link for more info:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Mounting_drives_and_.2Fetc.2Ffstab](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Mounting_drives_and_.2Fetc.2Ffstab)

---

