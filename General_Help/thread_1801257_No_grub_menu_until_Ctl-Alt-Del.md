---
title: "No grub menu until Ctl-Alt-Del"
date: 2011-07-10
forum: General Help
---

### Post by SalsaMeSalvo on 2011-07-10
Sorry if this has already been answered somewhere. I can't find the exact problem i have.

It's on 11.04, grub 1.99rc1. Single boot.

When i boot or restart, after the POST i get a blank, purple screen. It never moves to the grub menu.

If i wait a few seconds and Ctl-Alt-Del, the machine reboots and i get the grub menu after the POST, and everything is normal after that.

How can i make it so that it goes to the grub screen without having to Ctl-Alt-Del?

Thanks in advance for your time and help.

---

### Post by Ad@m on 2011-07-10
[http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)

This should be of help.

---

### Post by SalsaMeSalvo on 2011-07-11
> **Ad@m said:**
> [http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)

This should be of help.

Thank you very much. 

It did turn out to be the hidden timeout. I thought i had already set it right, but commenting GRUB_HIDDEN_TIMEOUT=0 was what finally fixed it. :D

---

