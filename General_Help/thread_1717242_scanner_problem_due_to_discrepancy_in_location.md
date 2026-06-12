---
title: "scanner problem due to discrepancy in location"
date: 2011-03-29
forum: General Help
---

### Post by haya on 2011-03-29
I have just installed the drivers for the scanner on my brother mfc5460cn.  Xsane recognizes the machine but cannot open due to an invalid argument.  The problem seems to be that xsane is looking for the machine at bus 1 dev 1 however, lsusb shows the machine at bus 2 dev 5.

How can I fix the discrepancy?  
I've tried sudo chmod a+w /dev/bus/usb  but there was no change.

Thanks in advance.

---

### Post by haya on 2011-03-31
I found the solution:
sudo chmod a+w /dev/bus/usb/$Bus/Dev

---

