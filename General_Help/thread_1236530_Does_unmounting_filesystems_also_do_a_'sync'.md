---
title: "Does unmounting filesystems also do a 'sync'?"
date: 2009-08-10
forum: General Help
---

### Post by CTBuckweed on 2009-08-10
I run 8.04 LTS (Hardy). I use a 4gig FAT32 USB stick for some of my files between Ubuntu & Windows. Sometimes, the USB stick is corrupted (according to Windows CHKDSK) and files are lost.

When I unmount the USB, (via a right click on the icon on the GNOME desktop), does the unmount selection also do a sync to the USB? I don't know for sure. I have been using 'sync' and waiting a bit before unmounting the USB. I haven't tried just an unmount and then pulling the USB out after it's unmounted.

My questions are:

1) Does the unmount also flush all I/O to the mounted drive / USB stick?

2) When in the command shell, does the 'sync' command not return to the command prompt until after all I/O is flushed?

---

### Post by decoherence on 2009-08-10
"Yes" to both.

---

### Post by CTBuckweed on 2009-08-10
Thanks decoherence, I'll test it out.

---

