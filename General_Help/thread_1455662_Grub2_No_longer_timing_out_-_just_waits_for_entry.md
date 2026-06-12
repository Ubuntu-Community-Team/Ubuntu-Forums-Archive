---
title: "Grub2: No longer timing out - just waits for entry"
date: 2010-04-16
forum: General Help
---

### Post by buchs on 2010-04-16
For some reason, grub2 (Karmic) has, intermittently, stopped timing out on a choice.  It doesn't count down.  It simply waits and I have to press a carriage return.  I rebuilt the grub database (mkgrub - I can remember the name) and it was of no avail.  Suggestions?

---

### Post by coffeecat on 2010-04-16
Have a look in your /etc/default/grub file. Are the first few lines like this?

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```... particularly the GRUB_TIMEOUT line.

> **buchs said:**
> I rebuilt the grub database (mkgrub - I can remember the name) 

mkgrub? :? Do you mean update-grub?

---

