---
title: "Cannot move files to trash/trash bin does not retain files"
date: 2010-07-23
forum: General Help
---

### Post by beanryu on 2010-07-23
Hello there,

When I try to move a file to trash, it doesn't retain anything.  I drag a file to the trash bin icon, I open the trash bin, its' empty.  How do I make my trash bin retain some trash?

Thanks in advance.

---

### Post by agnes on 2010-07-24
This would be normal if it were files on an external device, those are moved to a hidden folder (called e.g. .Trash) on that device itself.

If not, does it also not work with right click->move to trash; and do you also have nothing in ~/.local/share/Trash/ ? If you moved them e.g. as root, then they are in /root/.local/share/Trash.

---

