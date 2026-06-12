---
title: "remove floppy drive"
date: 2011-05-21
forum: General Help
---

### Post by pooper on 2011-05-21
How do I remove floppy drive, for some reason ubuntu lists it but I do not even have one installed and I also have it disabled in BIOS. 

"sudo modprobe -r floppy" works, but only temporarily 

I've already commented it out in fstab

---

### Post by tredegar on 2011-05-21
Put in the file **/etc/rc.local**, before the line that says **exit 0** this line

**modprobe -r floppy**

No **sudo** is required as that file is run as root.

Or you can "blacklist" the floppy module (feel free to search on blacklisting modules with ubuntu).

"Ubuntu" seems to be getting worse. At 8.04, it was excellent. Downhill from there it seems.

Hope this helps.

---

