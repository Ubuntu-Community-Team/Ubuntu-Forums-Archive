---
title: "Where did /proc/acpi/processor go?"
date: 2012-03-18
forum: General Help
---

### Post by futureishere on 2012-03-18
I have this Core i7 system which currently has Fedora 12 installed. On Fedora I have been playing around with acpi settings like throttling and frequency scaling for ages with no problems. Yesterday, I tried using booting the machine using bootable usb equipped with ubuntu 11.10. But I did not find processor directory in /proc/acpi/. Only /ac_adapter, /battery directories and event and wakeup files. I tried rebooting the liveusb with acpi=force, but that didn't work either. I tried looking for /proc/acpi/processor in the ubuntu 11.10 installed in my core i5 dell laptop and it's not there either. So my question is obvious? What happened to acpi processor settings?

---

### Post by 2F4U on 2012-03-18
As far as I understand it, /proc/acpi has been marked deprecated a long time ago

[http://www.h-online.com/open/features/Kernel-Log-Coming-in-2-6-36-Part-4-Drivers-1100878.html?page=2](http://www.h-online.com/open/features/Kernel-Log-Coming-in-2-6-36-Part-4-Drivers-1100878.html?page=2)

Maybe Fedora still keeps it due to several reasons, while Ubuntu removed it.

---

### Post by futureishere on 2012-03-19
Aah...thanks!

---

