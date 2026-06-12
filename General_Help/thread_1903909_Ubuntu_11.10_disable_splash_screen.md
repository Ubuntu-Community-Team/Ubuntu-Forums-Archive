---
title: "Ubuntu 11.10 disable splash screen?"
date: 2012-01-03
forum: General Help
---

### Post by Mr0wyx on 2012-01-03
Hello!

On system boot after grub menu it shows blank purple screen. Is it possible to remove that, so plain boot text will be displayed? I have modified /etc/default/grub and removed quite and splash and made update-grub but no changes.

Thank you!

---

### Post by dcstar on 2012-01-05
> **Mr0wyx said:**
> Hello!

On system boot after grub menu it shows blank purple screen. Is it possible to remove that, so plain boot text will be displayed? I have modified /etc/default/grub and removed quite and splash and made update-grub but no changes.


Check the /boot/grub/grub.cfg file and see if the boot strings have actually changed.

---

### Post by samant on 2012-01-10
I have Ubuntu 11.10 and want to see boot rows during system loading. I removed "splash" and "quite" from /boot/grub/grub.cfg. Animation (caption "Ubuntu" and blinking points below) actually was disabled, but I still see a violet screen instead of information rows about processes' loading. Does anybody have some advice for me? :)

---

