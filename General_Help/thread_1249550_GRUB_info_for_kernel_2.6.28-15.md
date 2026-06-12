---
title: "GRUB info for kernel 2.6.28-15"
date: 2009-08-25
forum: General Help
---

### Post by applecake on 2009-08-25
Hey! During my last update, I chose to not add the new boot info for kernel 2.6.28-15 in my menu.lst (GRUB). What info do I need to add for kernel 2.6.28-15?
Thanks! :)
/applecake

EDIT: Thank you! :)

---

### Post by tgeer43 on 2009-08-25
Edit menu.lst as root and just copy/paste an existing section from the previous kernel and replace all references to the old kernel number to the new one. eg. Change 2.6.28-14 to 2.6.28-15. There are three references to be changed. They are in the title, kernel, and initrd lines.

That's all there is to it!

tgeer

---

