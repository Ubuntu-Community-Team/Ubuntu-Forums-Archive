---
title: "Re-enable Ubuntu notifications system"
date: 2009-11-03
forum: General Help
---

### Post by jspidle on 2009-11-03
I disabled the Ubuntu notifications as per [http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/](http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/) sometime ago. I think Karmic is supposed to make the notifications less annoying, maybe. At least I want to give them a try.

I think I did both of the following:

```
sudo chmod -x /usr/lib/notification-daemon/notification-daemon
```

```
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled
```

How would I undo those commands?

Thanks,
Jason

---

### Post by drs305 on 2009-11-03
Although I can't verify this will restore it, the commands to reverse the ones you mention are:
```

sudo chmod +x /usr/lib/notification-daemon/notification-daemon
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled /usr/share/dbus-1/services/org.freedesktop.Notifications.service

```

I can't verify the success since I don't know if you did this on Karmic or previously on another release. If you upgraded since you executed those commands the files may have changed.

Added:
When I was experimenting with the notification daemon, the command I used to disable it was:
```
sudo chmod -x /usr/lib/notify-osd/notify-osd
```
To turn it back on, I changed "-x" to "+x"

---

### Post by undecim on 2009-11-03
```
sudo chmod +x /usr/lib/notification-daemon/notification-daemon
``````
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled /usr/share/dbus-1/services/org.freedesktop.Notifications.service
```

That should do it. Make sure first though that /usr/share/dbus-1/services/org.freedesktop.Notifications.service doesn't already exists. If it does, you shouldn't need to do that second part.

---

### Post by jspidle on 2009-11-03
I did both and notifications have returned.

```
sudo chmod +x /usr/lib/notification-daemon/notification-daemon
``````
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled /usr/share/dbus-1/services/org.freedesktop.Notifications.service
```The only problem now (don't know if this deserves a different thread) is that the notifications are showing up in the wrong place. See the screenshot, notifications are well below the notification panel for some reason.

---

### Post by jspidle on 2009-11-03
Nevermind, I see now that there is [another thread on this exact subject]("http://ubuntuforums.org/showthread.php?t=1303831"). This thread can be marked as solved, if that is actually something y'all do.

---

