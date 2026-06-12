---
title: "Disable Plymouth's quiet and splash ?"
date: 2011-07-14
forum: General Help
---

### Post by zami on 2011-07-14
How can I stop seeing the mauve (or any) splash screen?

How can I get back to seeing readable text, instead of this flashing of text and that awful 800x600 screen with the dots?

I tried:
in /etc/default/grub change
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="" 
then
sudo update-grub
No change.  I still see the mauve screen and dots and only flashes of text output.

I also read instructions on what to alter in
/boot/grub/grub.conf
but I have no such file.  (I have a grub.cfg but the interior looks very different than the grub.conf examples I've seen.)

Any further suggestions?

-Laura

---

