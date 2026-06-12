---
title: "Edit grub"
date: 2010-02-18
forum: General Help
---

### Post by joshh88 on 2010-02-18
I have been trying to edit grub to make windows vista the default but whne i got to the menu.lst it is blank.
I use this from the official guide gksudo gedit /boot/grub/menu.lst  and it still comes up blank as well as sudo gedit /boot/grub/menu.lst
Any ideas? Thanks

---

### Post by sisco311 on 2010-02-18
GRUB 2 is the default boot loader and manager for Ubuntu 9.10 (Karmic Koala).

You have to edit the /etc/default/grub file:
[thread=1302743][COLOR="Red"]Grub 2 - 5 Common Tasks[/COLOR][/thread]

[uhelp]community/Grub2[/uhelp]
[thread=1195275]The Grub 2 Guide[/thread]
[thread=1287602]Grub 2 Title Tweaks[/thread]

---

### Post by philinux on 2010-02-18
> **joshh88 said:**
> I have been trying to edit grub to make windows vista the default but whne i got to the menu.lst it is blank.
I use this from the official guide gksudo gedit /boot/grub/menu.lst  and it still comes up blank as well as sudo gedit /boot/grub/menu.lst
Any ideas? Thanks

If you are unfamiliar with editing grub or grub2 then for this purpose install startupmanager.

The menu item appears in system>admin. It is self explanatory when you run it.

---

