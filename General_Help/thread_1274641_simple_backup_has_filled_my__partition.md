---
title: "simple backup has filled my / partition"
date: 2009-09-24
forum: General Help
---

### Post by colinireland on 2009-09-24
Hello,

I have used simple backup to backup data stored on my / partition and my /home partition to a new external hard drive I bought today. However accidentally I pulled out the USB cable during the backup process and now my / partition is filled to capacity. Has simple backup created a temporary file somewhere on this partition? It went from 25% to 100%.

Can anyone tell me where these files might be located or can you tell me some other way I can get my hard drive space back.

Thanks
Colin

---

### Post by solitaire on 2009-09-24
check the /media/ directory.

I think if it was trying to save to /media/usb_drive/backups/  ("usb_drive" being the USB drive's root)
If you then pulled out the cable, it would create /media/usb_drive/backups/ on the root ("/") and keep filling up till it stops or runs out of room. (I think!!).

So unplug the USB drive and see what's in your /media/ folder....

---

### Post by colinireland on 2009-09-25
That worked perfectly solitaire, thanks!!!

---

