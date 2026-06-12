---
title: "Notification area?"
date: 2010-11-03
forum: General Help
---

### Post by Hangwire on 2010-11-03
Hi. Every time someone messages me in pidgin or my track changes in Amarok, or a theres a new update or a driver, this small popup thing appears below my clock and date. What is that, How do I get rid of it and can I customize where it appears? Its way too down right now.

EDIT: Ah-ha! There it is again. I made a screenshot, its attached. 
Any ideas?

---

### Post by Hangwire on 2010-11-03
Bump?

---

### Post by ivarn on 2010-11-03
you know how to customize the panels right?
click right click and "add to panel".
Right click in the area and click remove from panel.

---

### Post by Hangwire on 2010-11-03
Doesn't Work. It just gives me the right click menu for the program I'm using (browser) or the desktop.
BTW, when I move my mouse over it, it fades.

---

### Post by sikander3786 on 2010-11-03
Removing the notification area will also remove some more applets. Instead try

```
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled
```

And reboot. The OSD notifications should be gone.

If sometime later, you want to enable them, this will do it.

```
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled /usr/share/dbus-1/services/org.freedesktop.Notifications.service
```

---

### Post by ivarn on 2010-11-03
But then you can't restore it or anything.
Do you see the area that looks something like this:
¤                   ¤
¤ notifications ¤
¤                   ¤
right click on the ¤ looking thing. it looks like 3 small windows actually.
edit: no it's 4. sorry

---

### Post by Hangwire on 2010-11-04
> **sikander3786 said:**
> 

And reboot. The OSD notifications should be gone.

I just needed a name. Thank you for the post and details, and thanks to ivarn too for his time. 
Marked solved (:

---

### Post by yetiman64 on 2010-11-04
> **Hangwire said:**
> ...Marked solved (:
Ahh, not quite yet ;), you need to do that with the Thread tools drop down menu at the top of your browser window. 

Link #5 in my sig has instructions if needed. 

Only reason I checked this thread is because it wasn't marked as solved  in the main forum (and thought I may be able to help) :). Cheers from yetiman64.

---

