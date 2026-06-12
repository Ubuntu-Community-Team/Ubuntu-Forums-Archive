---
title: "Can anyone tell what my error message means?"
date: 2006-06-03
forum: General Help
---

### Post by Scorpuk on 2006-06-03
At the top of the page I get an error message: can anyone tell me how to fix it?

[My System]("http://scorpuk.plus.com/phpsysinfo")


tnx.

---

### Post by tonyr on 2006-06-03
I don't think it needs to be fixed.  It is a problem with whatever web based tool you are
using to generate the report.  It's not really an error, but an advisory message.   It is telling
 you that there is no file named **/proc/scsi/scsi** on your machine.   Such a file would
only exist if you had a SCSI controller (or maybe a USB device, which can look like a SCSI
device) on your system.  The tool should be smart enough to know whether or not you
have a SCSI controller, and should be able to tell the difference between a USB device
that looks like a SCSI device, and a real SCSI device.  That it does not is the fault
of the tool writers, not your system.

---

