---
title: "No GUI at Startup"
date: 2009-10-09
forum: General Help
---

### Post by jim78 on 2009-10-09
I was messing around with my ubuntu installation the other day and have disabled gnome at startup and don't know how to start it back up again. I ran this command in a terminal to stop it: > sudo update-rc.d -f gdm remove

I can run it (gdm) from text only mode but it's a pain logging in only to launch gnome and log in again. I use this to launch it from text only: > sudo /etc/init.d/gdm start - start gnome

Can someone tell me what I have to edit to get it to automatically boot gdm from startup? 

Thanks.

---

### Post by wojox on 2009-10-09
Try this:

```
sudo update-rc.d gdm defaults 13 01
```

---

### Post by jim78 on 2009-10-09
prefect, thanks. What is rc.d?

---

### Post by wojox on 2009-10-09
Their scripts that control services.

---

