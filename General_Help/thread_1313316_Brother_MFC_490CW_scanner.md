---
title: "Brother MFC 490CW scanner"
date: 2009-11-03
forum: General Help
---

### Post by weverjames on 2009-11-03
I need help to have the scanner working. I already got the printer working. However I have not been able to get the scanner working. I downloaded the driver from brother website: brscan3. I followed the instructions about editing the file system. But still getting the " device not available" when starting xsane.
I had the same printer/scanner working in Ubuntu 9.04. I wanted to upgrade to karmic and this is the only thing that is making the move difficult.

---

### Post by jbg144 on 2009-11-03
I had a similar problem with a Brother MFC 5490CN.
Printer installed without a hitch following instructions from Brother.
Scanner...would only be recognized if run as root.
The change recommended by Brother to file:
/lib/udev/rules.d/50-udev-default.rules
(i.e., changing libusb device nodes to mode=666) did not solve the problem
However, if you also change the last line under #printer to mode=666, the scanner will work properly for a non-root user.

---

