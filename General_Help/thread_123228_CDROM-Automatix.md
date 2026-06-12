---
title: "CDROM-Automatix"
date: 2006-01-29
forum: General Help
---

### Post by sda on 2006-01-29
Hello!

I installed a couple of things yesterday with Automatix, but I would like to remove the enabaling of the ejection of a cd with the CDROM drive button. Is there a way to go back to the Ubuntu way?

Also, would you guys recommend me the best programs for viewing pictures/audio from a cd?

Thanks

---

### Post by dcstar on 2006-01-29
[QUOTE=sda]Hello!

I installed a couple of things yesterday with Automatix, but I would like to remove the enabaling of the ejection of a cd with the CDROM drive button. Is there a way to go back to the Ubuntu way?
.......[/QUOTE]
Check your /etc/sysctl.conf file, if there is a line that says:

dev.cdrom.lock = 0

Then comment it out or set it to "1" (or delete it!).

---

