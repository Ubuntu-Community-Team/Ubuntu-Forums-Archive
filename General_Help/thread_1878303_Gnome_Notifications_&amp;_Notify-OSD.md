---
title: "Gnome Notifications &amp; Notify-OSD"
date: 2011-11-09
forum: General Help
---

### Post by zipmon on 2011-11-09
Hi everybody!

I'm running Oneiric with Gnome Shell as my main DE, and everything works fantastic except for some strange behaviour with notifications: on some days (log-ins), I have the standard Gnome 3 notifications (popping up at the bottom of the screen), and on other days I'm greeted by the Notify-OSD style notifications, the cursor shy bubbles appearng in the top-right of the screen. The two systems never mix from startup to startup and they both work perfectly fine; I just prefer the native Gnome ones and wondered if anyone knew how to make sure they get loaded instead of NotifyOSD! (I'm not keen on deleting NotifyOSD though, since I do use Unity from time to time and would like them to work there.)

Thanks so much!!

---

### Post by notgary on 2011-11-10
I'm not sure if there's an elegant and automated way to do this, but you can disable NotifyOSD by renaming the following file:

```
/usr/share/dbus-1/services/org.freedesktop.Notifications.service
```to anything at all, so

```
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled
```will disable the service, and renaming it back using 

```
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled /usr/share/dbus-1/services/org.freedesktop.Notifications.service
```will re-enable it. If you stick both of them in separate scripts you can quickly enable and disable NotifyOSD as and when you need it, and if you're only going into Unity from time to time, then it shouldn't be too much in your way.

---

### Post by zipmon on 2011-11-10
Thank you!! That was exactly the kind of trick I was looking for! Appreciate it! :)

---

### Post by notgary on 2011-11-10
No problem at all :)

---

