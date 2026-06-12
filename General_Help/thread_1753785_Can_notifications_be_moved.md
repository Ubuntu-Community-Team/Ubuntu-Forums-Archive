---
title: "Can notifications be moved?"
date: 2011-05-09
forum: General Help
---

### Post by searayman on 2011-05-09
In ubuntu Natty with the notification pop ups like for when the song changes in Banshee, they are in my top right corner.

Is there anyway to move them?

---

### Post by TheNerdAL on 2011-05-09
try 
```
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled
```

and restart.

---

### Post by searayman on 2011-05-09
> **TheNerdAL said:**
> try 
```
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled
```

and restart.

what does that due exactly does it disable the notifications?

---

### Post by Aenima99x on 2011-05-09
They can now be completely customized, see [here]("http://www.webupd8.org/2011/05/configurable-notifyosd-bubbles-for.html")

---

