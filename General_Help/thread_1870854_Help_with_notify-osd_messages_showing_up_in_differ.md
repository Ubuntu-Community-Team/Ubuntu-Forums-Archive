---
title: "Help with notify-osd messages showing up in different places in Oneiric?"
date: 2011-10-28
forum: General Help
---

### Post by inameiname on 2011-10-28
Here is my issue. In Ubuntu 11.10, for some reason notify-osd messages I do in 'sudo' versus messages I don't do in 'sudo' appear in different places. The 'sudo notify-send "whatever"' ones appear at the top right, just like they did in 11.04. However, messages without the 'sudo', 'notify-send "whatever"', appear in a traybar at the bottom.

Both pop up just fine, and then go away, but are just in different places. One further issue, however, is the 'non-sudo' ones that I do, which go on the bottom, after they pop up for a spell, actually remain in the traybar until I manually remove each and every one.

One thing to note, I did install a gnome-shell extension called gnome2-notifications. Would that have something to do with it? Perhaps why the 'sudo' ones work the way they used to, as they did in 11.04? If so, how would I change the others? Or vice versa?

I just want that traybar to stop keeping ALL messages, and to have ALL my messages in one place, on the top right, or at the bottom.

---

### Post by crdlb on 2011-10-28
GNOME Shell has an integrated notification daemon. That is what displays the messages at the bottom. When you run 'sudo notify-send', it appears that a new dbus session bus is created for root. Within this session, there is no service on org.freedesktop.Notifications, so one is bus-activated. In your case, it seems to be notify-osd, in mine it was notification-daemon. (This is governed by /usr/share/dbus-1/services/org.freedesktop.Notifications.service).

If that wasn't just a test, you shouldn't be sending notifications as root anyway. To your complaint about the notifications sticking around, this is due to gnome-shell making notifications persistent by default. You can set a "transient" hint on notifications, or you can replace old notifications when they are superceded (this is difficult or impossible to do with notify-send iirc)
```
notify-send --hint int:transient:1 Foo
```

---

### Post by inameiname on 2011-10-28
> **crdlb said:**
> GNOME Shell has an integrated notification daemon. That is what displays the messages at the bottom. When you run 'sudo notify-send', it appears that a new dbus session bus is created for root. Within this session, there is no service on org.freedesktop.Notifications, so one is bus-activated. In your case, it seems to be notify-osd, in mine it was notification-daemon. (This is governed by /usr/share/dbus-1/services/org.freedesktop.Notifications.service).

If that wasn't just a test, you shouldn't be sending notifications as root anyway. To your complaint about the notifications sticking around, this is due to gnome-shell making notifications persistent by default. You can set a "transient" hint on notifications, or you can replace old notifications when they are superceded (this is difficult or impossible to do with notify-send iirc)
```
notify-send --hint int:transient:1 Foo
```


Thanks for the information. I think I understand all that. It is just a shame I cannot easily move all of the notifications back to the top right, where they were in past Ubuntu versions. I thought the plugin, gnome-shell-gnome2-notifications (later renamed gnome-shell-classic-systray: [https://github.com/rcmorano/gnome-shell-gnome2-notifications](https://github.com/rcmorano/gnome-shell-gnome2-notifications)) would change things back to the way they were, but I don't believe it is working for me. I'll keep playing with it. Although, regarding this particular gnome-shell extension, as I am fairly unclear of just what it does, it may not do anything here at all, just put actual icons in another spot. :P

Oh, and as for using 'sudo' in a notify-osd message, you are right, it isn't something that one should do. I only realized this fact not in my tests, but by noticing some messages (namely those I included in custom debian packages I have and install) would show the notify-osd message in the top right rather than the now norm, middle bottom.

And thanks for the help on the bottom tray. I will try that code you gave, but it sounds like it only stops specific messages (ie, your use of 'Foo' in the code). Does that mean for every since one I have to manually put in that code to make it stop doing others just like it? If so, yikes. Also, I have udev-notify installed, numerous user-made notify-osd messages in various packages and programs that each have their own thing.

---

### Post by crdlb on 2011-10-28
That extension appears to move tray icons up to the system status area. It should have no effect on actual libnotify notifications.

Changing the default semantics of notifications (from transient to persistent) is unfortunate, but I can sort of understand why they did it. You may be able to patch gnome-shell's notificationDaemon.js to make notifications transient by default, but the long-term solution is to file bugs against software that doesn't set the transient hint or replace existing notifications when appropriate.

---

### Post by inameiname on 2011-10-28
> **crdlb said:**
> That extension appears to move tray icons up to the system status area. It should have no effect on actual libnotify notifications.

Changing the default semantics of notifications (from transient to persistent) is unfortunate, but I can sort of understand why they did it. You may be able to patch gnome-shell's notificationDaemon.js to make notifications transient by default, but the long-term solution is to file bugs against software that doesn't set the transient hint or replace existing notifications when appropriate.

I see. So that extension moves icons that would normally be placed on the bottom traybox (along with those notify-send messages) onto the top main system bar, in the system status area? I think I got that. So it does seem to be a useful one, then. I was curious about that.

Now, as for the notify-send messages, I too can understand their desire to retain them. Handy to have in case you didn't catch it the first time. Of course, that said, some aren't too special. There really needs to be a way to diagnose the important ones to save and retain, versus the unimportant ones. Anyway, I will be sure to look into the notifyicationDaemon.js. I'll just have to figure out how. :P

Overall, I don't mind the bottom traybox, other than the retaining of the messages. Although, one flaw I've noticed is when a message does come up from there, it only pops up the first part of it, unlike the old-school top right ones, which showed you all of the message.

---

### Post by crdlb on 2011-10-28
> **inameiname said:**
> Although, one flaw I've noticed is when a message does come up from there, it only pops up the first part of it, unlike the old-school top right ones, which showed you all of the message.

That's an attempt to make notifications less distracting. It only displays the title by default. You can choose to read the full message by hovering over it, or you can ignore it.

---

### Post by inameiname on 2011-10-29
> **crdlb said:**
> That's an attempt to make notifications less distracting. It only displays the title by default. You can choose to read the full message by hovering over it, or you can ignore it.

Ah. Well, as most notify-osd messages I ever get aren't too long, it'd be extra work to move and hover over it within the 3 seconds the notification is up (I use Leolik's notify-osd). Oh well; I'll have to figure something out. Again, shame I just cannot switch all of them back to the top right like in previous Ubuntu versions, and completely get rid of that bottom traybox.

---

