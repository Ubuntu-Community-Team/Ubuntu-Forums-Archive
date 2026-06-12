---
title: "grub.cfg overriden on kernel update"
date: 2011-06-13
forum: General Help
---

### Post by arcull on 2011-06-13
Hi guys. On my laptop running Ubuntu 10.04 I have edited /boot/grub/grub.cfg in order for the shortcut keys for changing brightness and volume to work. I added ```
acpi_osi=Linux
``` at the end of every kernel image line, and it works ok. The only problem is that every kernel update overrides the grub.cfg and therefore I have to reedit the file over and over again. So the question is, where could I put the mentioned kernel startup parameter, so that it doesn't get lost on every kernel update. Thanks for your suggestions in advance.

---

### Post by Elfy on 2011-06-13
Try adding it to the GRUB_CMDLINE_LINUX line in /etc/default/grub and running sudo update-grub

[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

---

### Post by arcull on 2011-06-13
Will give it a try and report back, much thanks for info :)

---

### Post by arcull on 2011-07-24
Works as forestpiskie suggested, thanks again.

---

