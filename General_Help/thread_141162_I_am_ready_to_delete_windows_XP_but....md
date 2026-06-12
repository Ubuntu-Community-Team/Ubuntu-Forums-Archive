---
title: "I am ready to delete windows XP but..."
date: 2006-03-07
forum: General Help
---

### Post by beast2k on 2006-03-07
If I delete windows XP from hda1 will that not kill the master boot record? and prevent me from booting linux ? Windows has never really been totally gone from my system (I havent used it in almost a year) so I have no way of knowing what effect deleting windows  will have on linux. BTW by deleting I mean formating hda1 as ext3 and use it for storing backups. If it does kill the MBR where do I install grub to? if the MBR of hda1 is gone ? I could make hdb bootable but i dont know if that will mess things up. Can somebody please shed some light on what effect deleting windows will have on linux and what the best course of action is? Thank you in advance:confused:

---

### Post by el3ktro on 2006-03-07
Short answer: NO, your MBR will NOT be killed, it's stored at the very beginning of the harddisk, not inside any partition.

Tom

---

### Post by beast2k on 2006-03-07
[QUOTE=el3ktro]Short answer: NO, your MBR will NOT be killed, it's stored at the very beginning of the harddisk, not inside any partition.

Tom[/QUOTE]
Awesome, thats the answer I was hoping for but I coulden't find it in any forum even though a search for "deleting windows" brings up hundreds of results. Thanks for the quick answer; now if you'll excuse me I'm off to create hd space at microsofts expence. Thanks again.\\:D/

edit:I just deleted it, changed fstab, adjusted grub now I'm windows free. Somehow I feel a big relief like a weight has been lifted.

---

### Post by StefanoCole on 2006-03-08
> now I'm windows free.

Well done! :KS

---

### Post by cotcot on 2006-03-08
For the case you still have XP in the boot menu and do not know how to delete it from the menu :

Edit /boot/grub/menu.lst : delete the lines of the XP boot.

---

### Post by beast2k on 2006-03-08
[QUOTE=cotcot]For the case you still have XP in the boot menu and do not know how to delete it from the menu :

Edit /boot/grub/menu.lst : delete the lines of the XP boot.[/QUOTE]

Thanks for the info but I knew about fstab and grub but either didnt know about the mbr in a partition or I used to know and just forgot. It feels strange using a PC knowing there is no windows to fall back on, kind of like tight rope walking with a net for years and finally cutting the net away then later finding out you never really needed the net because you were always only a few feet off the floor.
BTW shoulden't the instructions on how to safely delete windows be clearly posted seeing how thats what we want everyone to do ?

---

