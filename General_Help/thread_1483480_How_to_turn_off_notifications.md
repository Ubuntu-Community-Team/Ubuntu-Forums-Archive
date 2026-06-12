---
title: "How to turn off notifications"
date: 2010-05-14
forum: General Help
---

### Post by rmcellig on 2010-05-14
How can I turn of my Pidgin notifications as well as all other notifications that pop up? I am running Ubuntu as well as Xubuntu.

---

### Post by kerry_s on 2010-05-14
just uninstall "notify-osd"

---

### Post by rmcellig on 2010-05-14
I will do that. Thanks!!

 Would you know if there is a way to turn it off without uninstalling it? Maybe a small GUI app or something similar?

---

### Post by kerry_s on 2010-05-14
> **rmcellig said:**
> I will do that. Thanks!!

 Would you know if there is a way to turn it off without uninstalling it? Maybe a small GUI app or something similar?

no, if anything calls it, it's restarted.

edit: 
wait, you can try setting it not executable.
in terminal:
**sudo chmod -x /usr/lib/notify-osd/notify-osd**

---

