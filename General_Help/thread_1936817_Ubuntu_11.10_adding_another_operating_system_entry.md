---
title: "Ubuntu 11.10: adding another operating system entry to grub"
date: 2012-03-06
forum: General Help
---

### Post by gmskel on 2012-03-06
Grub does not detect the third operating system on my hard drive, which is Windows XP.
The grub menu contains entries for Ubuntu 11.10, and Windows 7 but, no entry for Windows XP.
I have entered a line in the grub.cfg file that is supposed to detect Windows XP. But it didn't work.

How can I get Windows XP detected by grub?

---

### Post by gmskel on 2012-03-06
Issue resolved.
I simply copied the settings for detecting Windows 7 and changed the appropriate lines.

---

