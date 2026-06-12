---
title: "remove update notification"
date: 2012-01-15
forum: General Help
---

### Post by layers on 2012-01-15
Hey, I have disabled any sort of updates as possible, but this update notification always pops up, eventhough I right click it, and there is no checkmark beside "show updates"

more info: this notification says: The update information is outdated. This may be caused ...

How can I make it go away?

---

### Post by BC59 on 2012-01-15
The permanent solution but loosing the update notifications for ever is to run from a terminal

```
gksudo nautilus /etc/xdg/autostart
```

and from this folder delete the entry for update notifications.

---

### Post by layers on 2012-01-15
thank you

---

