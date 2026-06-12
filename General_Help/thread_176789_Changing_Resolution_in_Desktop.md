---
title: "Changing Resolution in Desktop"
date: 2006-05-15
forum: General Help
---

### Post by hotbrainz on 2006-05-15
In the dapper 6.06 , I installed the server. At first it did not have a graphical user interface( gui ) but i got it running with some scratching around. But the resolution seems fixed at the lowest 640x.. 

The other options show but when i select it no changes happen
Please help. This low resolutioon is seriously bothering me now!

Thanks a ton in advance...

Any innovative suggestions will do.. i am despo for some thing..

---

### Post by kb3hkg on 2006-05-15
try looking into your xorg.conf file. In there you can force a change by changing the resolution.

---

### Post by KillrBuckeye on 2006-05-15
How did you get the X server running?  Are you using the proper video drivers, or did you have to resort the the VESA driver?  If you are using the proper driver, follow kb3hkg's suggestion of editing your xorg.conf to include the desired resolution on the "Modes" line under the proper color depth section.

---

