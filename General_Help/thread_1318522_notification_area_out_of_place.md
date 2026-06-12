---
title: "notification area out of place"
date: 2009-11-07
forum: General Help
---

### Post by jack handy on 2009-11-07
this happened pretty much overnight, without any changes on my part to the system:

[IMG]http://imgur.com/RgRUN.jpg[/IMG]

i tried just removing the notification area from the taskbar, creating a new taskbar, whatever.  problem still persists. 

anyway to fix this? or maybe just turn it off completely since i don't really care for this feature anyway. 

thanks

---

### Post by drs305 on 2009-11-07
To change the location, you might try installing and running this:
```
sudo apt-get install notification-daemon
notification-properties
```
Locations are also available via the gconf-editor (gconf-editor /apps/notification-daemon/popup_location)

You can turn it off with this command:
```
sudo chmod -x /usr/lib/notify-osd/notify-osd
```
or , rename service
```
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled 
```

---

### Post by Xenomorph on 2009-11-07
The location bothers me too.

This is the first thing I've been searching for to "fix" with Ubuntu 9.10.

The "notification-properties" doesn't seem to have anything to do with the new notification system in Ubuntu 9.10.

---

### Post by kostkon on 2009-11-07
It's a feature, not a bug, and it can't be changed. Low priority notifications appear lower than the high priority ones.

---

### Post by Xenomorph on 2009-11-07
Ok, I found a fix!

[http://www.webupd8.org/2009/10/things-to-fix-tweak-after-installing.html](http://www.webupd8.org/2009/10/things-to-fix-tweak-after-installing.html)

There is a DEB package provided that installs an updated notify-osd.

The notification "bubbles" are now right under the top bar, instead of way below it.

---

### Post by cusinndzl on 2010-03-27
My notifications appear too high. And that package just made them higher.

---

