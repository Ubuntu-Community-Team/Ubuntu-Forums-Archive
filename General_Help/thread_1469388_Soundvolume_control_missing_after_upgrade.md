---
title: "Sound/volume control missing after upgrade"
date: 2010-05-02
forum: General Help
---

### Post by whitefort on 2010-05-02
I'd be really grateful if anyone could give me some idea where to look for a solution to this.

Since doing an upgrade from Koala to Lynx, my volume control (up in the top right corner of the screen) has vanished.  I can still mute and control volume by going into the Sound menu in Preferences, but I really miss having it on the taskbar.

Any idea how to get it back?

Thanks!

---

### Post by prshah on 2010-05-02
> **whitefort said:**
> my volume control (up in the top right corner of the screen) has vanished. 

The volume control icon is part of the indicator applet; maybe that is not running for you? Check with ```
ps -e|grep indicator-app
``` in a Terminal (Applications-Accessories-Terminal) or just try adding it with by right clicking a blank area of the panel and choosing "Add to panel" -> "Indicator Applet"

---

### Post by whitefort on 2010-05-02
Eek!

Now I feel REALLY stupid!!

That was it.  I was convinced it was running, and was messing around in gconf-editor and all sorts of places trying to figure it out.

No idea why it stopped running, but all's fixed now. 

Thanks!

---

