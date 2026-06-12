---
title: "Ubuntu Live Buffer I/O error on device Fd"
date: 2009-08-18
forum: General Help
---

### Post by Spaz007 on 2009-08-18
When trying to boot from a USB stick of Ubuntu Live. I get the error Buffer I/O error on device Fd. It basiclly just displays that error over and over never finishing. I refomatted And reinstalled the live image but no go. Any idea on why this comes up?

---

### Post by spcwingo on 2009-08-18
Sounds like it's trying to read from a floppy (fd0).  Try entering BIOS and disabling the floppy controller.

---

### Post by riazrahaman on 2009-08-18
Can you please share the log messages?

Is it been seen when you do a dmesg?

---

