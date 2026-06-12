---
title: "usb busy - nautilus"
date: 2010-08-01
forum: General Help
---

### Post by scotch_neat on 2010-08-01
Hi there.

I'm trying to "Safely Eject" my USB mem stick and am getting:

"Volume is Busy" 

and it's showing that it's the application:

x-nautilus-desktop

as the culprit.

Should I should down the Nautilus process? How can I unmount/eject the stick?

Thanks

---

### Post by corrytonapple on 2010-08-01
Make sure no files are being used or are being transferred or copied. If not, you could just unplug it. Shouldn't hurt it.

---

### Post by kgas on 2010-08-01
check with lsof to see which application is holding the usb then close all those and try unmounting the volume.

---

