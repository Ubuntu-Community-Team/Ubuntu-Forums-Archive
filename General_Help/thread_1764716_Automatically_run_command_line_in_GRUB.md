---
title: "Automatically run command line in GRUB"
date: 2011-05-22
forum: General Help
---

### Post by zhi hao on 2011-05-22
Hi all,

I have an LG E300 that's about 2-3 years old. I have recently purchased a new computer but would like to install Ubuntu on my LG and keep it as a backup, but I have some problems.

Somehow, the only way for my keyboard to work in Ubuntu is to run these two command lines in GRUB:

i8042.dumbkbd=1
i8042.nopnp=1

I find it very irritating to key it in everytime I start up my computer. Is there a way around this?

PS I am using 11.04. Thanks in advance!

---

### Post by ajgreeny on 2011-05-22
```
gksu gedit /etc/default/grub
``` will open that file as root and you can then add those two lines separated by spaces to the end of the line, so
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
becomes
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR=Red]your commands[/COLOR]"

---

