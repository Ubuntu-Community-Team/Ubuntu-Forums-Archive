---
title: "Repeat Entries in &quot;Open With&quot; Menu"
date: 2009-12-19
forum: General Help
---

### Post by mercerudy on 2009-12-19
In the dialog box that appears after right-clicking a file, then selecting "Open With" -> "Other Application..." I have multiple repeat entries of several applications.  How can I fix this?

I've tried going into the properties menu and deleting the applications from the list, but that only affects the applications in the context menu, not the dialog box I've described.

I've attached a screenshot to help explain what I'm talking about.

Thanks in advance everyone.

---

### Post by hugmenot on 2009-12-20
Probably some duplicated .desktop files around on your system. Perhaps you can delete some off them.

---

### Post by nubalci on 2009-12-20
You can just select the entry you want and click the "Remove" button. Doesn't that do the job?

---

### Post by mercerudy on 2009-12-20
> You can just select the entry you want and click the "Remove" button. Doesn't that do the job? That would be the obvious choice, wouldn't it? :P

Sorry I did not mention this before, but the "Remove" button is grayed out for some reason, even while I have an entry selected.  Could someone let me know why?

Thanks.

---

### Post by dalesd on 2009-12-22
I have the same issue.  Duplicate entries in the "Open With" menu and the Remove button is grayed out.

---

### Post by 5n4K3 on 2010-01-20
Same issue here :( "Open With" needs revisiting.

---

### Post by Zorael on 2010-01-20
Have you tried renaming your **~/.local/share/applications** and **~/.local/share/mime** directories? Assuming this is caused by some weirdness in your user's settings, that should make it fall back onto the system-wide .desktop files.

---

