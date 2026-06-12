---
title: "Removing An Icon"
date: 2006-04-22
forum: General Help
---

### Post by morbid_bean on 2006-04-22
I would like to know how to remove the floppy icon off my desktop so i dont have to see it there. want to do is access the floppy from Places > Computer only...how do i go about doing this......yes i have mounted my drive, please help.

---

### Post by Ramses de Norre on 2006-04-22
All drives mounted under /media/ have an icon automaticaly, so if you want do delete just the floppy icon maybe the best way is editing fstab (and mount it under /mnt for example). If you want to remove all such icons: gconf-editor /apps/nautilus/desktop and uncheck icons_visible.

---

### Post by aysiu on 2006-04-22
Go to Applications > System Tools > Configuration Editor > Apps > Nautilus and you should see some option about what appears on the desktop somewhere in there.

---

