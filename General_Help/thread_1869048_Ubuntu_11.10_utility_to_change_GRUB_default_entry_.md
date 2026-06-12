---
title: "Ubuntu 11.10: utility to change GRUB default entry BROKEN"
date: 2011-10-25
forum: General Help
---

### Post by Panna-cakkhu on 2011-10-25
I don't know if it's only on my install but the recommended method to change grub default entry [in the official documentation]("https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2") doesn't work:
```
sudo grub-set-default "Whatever Ubuntu or Windows menu entry i copied from grub.cfg"
sudo grub-update
```
does not modify a single thing in /etc/default/grub.

But pasting the same "Whatever Ubuntu or Windows menu entry i copied from grub.cfg" directly in /etc/default/grub followed by
```
sudo grub-update
```
works perfectly.

Another thing broken in Ubuntu 11.10?

---

### Post by Panna-cakkhu on 2011-10-27
Ok that's actually a bug reported [here]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/543834"). The solution as described there is to set the GRUB variable GRUB_DEFAULT to *saved* in /etc/default/grub:
```
GRUB_DEFAULT=saved
```
Otherwise grub-set-default and grub-reboot will fail silently.

---

