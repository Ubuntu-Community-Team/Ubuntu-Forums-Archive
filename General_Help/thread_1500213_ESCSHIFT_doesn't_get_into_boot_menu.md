---
title: "ESC/SHIFT doesn't get into boot menu"
date: 2010-06-02
forum: General Help
---

### Post by hangfire on 2010-06-02
I've already joined the bug report on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/425979").

What I want to know here is:

How to I reboot directly into the GRUB menu, forced, without having to rely on the buggy sensing of the SHIFT key?

I've heard mention of some variables that can be set, but the 137 mostly nested lines of grub.cfg don't exactly encourage me to experiment.

Thanks.

---

### Post by JoelOl75 on 2010-06-03
You can set the grub menu to always come up instead of remaining hidden.  Just edit the file /etc/default/grub

sudo nano /etc/default/grub

and then run update-grub to set the changes

sudo update-grub

You should never modify the /boot/grub/grub.cfg file as any update to a kernel will overwrite the changes.  All modifications to how grub works should be changed in the /etc/default/grub file.  Any changes on what grub lists should be changed in the /etc/grub.d directory.  Following any modifications in either area a sudo update-grub will set the changes.

---

