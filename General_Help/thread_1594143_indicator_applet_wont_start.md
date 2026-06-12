---
title: "indicator applet wont start"
date: 2010-10-12
forum: General Help
---

### Post by l32007 on 2010-10-12
I cant get the wireless working now because i cant enable the notification area. is there another way to get the wireless manager to start or even better fix the applet?

---

### Post by akoskm on 2010-10-12
> **l32007 said:**
> I cant get the wireless working now because i cant enable the notification area. is there another way to get the wireless manager to start or even better fix the applet?

You can add the indiator-applet to your panel and install the package
```

sudo aptitude install indicator-network

```
to manage your wireless connections.
Eventually can try to delete your panel, to create a new one and add the "Notification Area" applet again.
Hope this help.

---

