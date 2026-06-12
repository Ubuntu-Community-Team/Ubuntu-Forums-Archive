---
title: "Brightness fix in karmic"
date: 2009-10-31
forum: General Help
---

### Post by bigpond on 2009-10-31
hey guys, i recently install karmic 64bit and i want to do the brightness fix by adding:

noapic to a line in /boot/grub/menu.lst

however i cant seem to find it, has it been moved? does anyone know where it is?

thanks for any help:D

---

### Post by frdrx on 2009-10-31
With grub2, adding kernel boot parameters is slightly more complicated. You should no longer edit the main configuration file ([FONT="Courier New"]/boot/grub/grub.cfg[/FONT]) directly. Instead, open [FONT="Courier New"]/etc/default/grub[/FONT] for editting and add the name of your parameter to the GRUB_CMDLINE_LINUX_DEFAULT variable. The result should read something like: `[FONT="Courier New"]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic"[/FONT]'. After you've saved the file, run the command `[FONT="Courier New"]sudo update-grub[/FONT]' to re-generate [FONT="Courier New"]/boot/grub/grub.cfg[/FONT].

---

### Post by bigpond on 2009-11-01
hey, thanks for the reply

I successfully found and edited the file, but i cant save because it says its read only

any ideas?

---

### Post by bigpond on 2009-11-01
Dont worry, sorry i was editing the wrong file :D

Thanks for the help!!

---

