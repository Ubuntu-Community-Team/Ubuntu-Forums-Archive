---
title: "Problem with indicators, Gwibber and Sound Preferences"
date: 2011-01-04
forum: General Help
---

### Post by nicocarbone on 2011-01-04
Hi. I am having a weird problem with my Ubuntu setup. My English is a bit rusty, so forgive me if my description of the problem is a bit convoluted.

I have configured Gwibber to autostart, working with a single Twitter account. Gwibber appears to startup correctely (notifications with unread tweets appears immediately when I turn on the PC), but it does not place itself in the indicator-messages (there is no little arrow to the left of Gwibber). After that, when I open Gwibber, it still not places itself in indicator-messages, instead it creates a tray icon (as it used to be in old versions of Ubuntu). I have to close it, and open it again and then the arrow appears in indicator-messages. From there on, it works OK, until the next restart, of course.

Another problem, probably related to the previous one, is that when I open the Sound Preferences (I am not sure it is the exact name of this item, I am using the spanish version of Ubuntu) from indicator-sound, it opens the preferences dialog and gnome-volume-control-applet which places a tray icon in the same way as Gwibber (again, like the sound tray icon in older versions of Ubuntu, and completely functional, with volume bar included).

I don't know where to start in order to debug this problem. It started around the last week, but I don't recall installing any package that may affect Ubuntu in this way. 

Anyone have/had the same problem? Any ideas to solve it?

Thanks you very much

---

### Post by nicocarbone on 2011-01-04
Me again. I've been investigating this problem and I have some now info.

The gwibber problem is solved if the indicator-applet process is killed and restored. May be Gwibber is starting before indicator-applet is properly initialized?

The Sound Preferences problem is associated with the fact that gnome-volume-control-applet is started when opening the Sound Preferences dialog. I checked others Ubuntu PCs, and mine is the only one showing this behavior. Any ideas?

---

### Post by nicocarbone on 2011-01-04
I solved the Sound Preferences problem deleting gnome-volume-control-applet.desktop from /etc/xdg/autostart. I am not sure if this is a good idea, but not I did not see any collateral damage so far.

Still having the problem with Gwibber, any idea will be welcomed.

---

### Post by nicocarbone on 2011-01-05
I solved the Gwibber problem. I edited the file "/etc/xdg/autostart/gwibber.desktop" and changed the value of "X-GNOME-Autostart-Delay" from 30 to 5.

---

