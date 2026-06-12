---
title: "Grub2 GRUB_CMDLINE_LINUX_DEFAULT options only apply to first entry?"
date: 2011-03-29
forum: General Help
---

### Post by martin_legion on 2011-03-29
Hello. I have installed Ubuntu Maverick and Arch linux, using grub from the Ubuntu installation.
I need to add "nomodeset" to the kernel parameters, so I do so in /etc/default/grub like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

then run update-grub, and everything ok, no errors or anything.

The problem is that actually, if I edit each entry of the menu, I see that the first one (ubuntu) has the options indicated in GRUB_CMDLINE..., but the entry for Arch Linux doesn't...
Is this a bug?
I need to add nomodeset to every entry in the menu.

Thanks!

---

### Post by QLee on 2011-03-29
> **martin_legion said:**
> Hello. I have installed Ubuntu Maverick and Arch linux, using grub from the Ubuntu installation.
I need to add "nomodeset" to the kernel parameters, so I do so in /etc/default/grub like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

then run update-grub, and everything ok, no errors or anything.

The problem is that actually, if I edit each entry of the menu, I see that the first one (ubuntu) has the options indicated in GRUB_CMDLINE..., but the entry for Arch Linux doesn't...
Is this a bug?
I need to add nomodeset to every entry in the menu.

Thanks!
Okay, you've added a kernel option to the "default" linux install, what happens when you add a kernel option to the next line? GRUB_CMDLINE_LINUX="" in /etc/default/grub and then update grub?

---

