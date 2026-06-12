---
title: "Power Button icon missing"
date: 2010-05-01
forum: General Help
---

### Post by halfsoul on 2010-05-01
I'm hoping someone can help me restore the Power Button icon/menu from the right of the top panel.  It disappeared after an error, and I haven't been able to restore it since.

Brief history:
1. Running Ubuntu since 9.04
2. Installed Ubuntu Studio & RT kernel ~1 week ago
3. While working with audio (Jack, Rosegarden, Hydrogen), the computer became unresponsive -- mouse would move but button clicks went unrecognized
4. Tried to close programs - no response
5. Tried to click on the Power Button to shutdown/restart, but no immediate response.  After a second or so, the power button disappeared.  Then after a few more seconds the computer shut down
6. After a reboot, things are functioning normal, except that the power button is still missing.
7. Upgraded to 10.04 = still missing
8. Restored panel to default = still missing
```

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```
9. Restored panel again w/ different instructions = still missing
```

gconftool --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

Any ideas?

Thanks in advance.

---

### Post by wojox on 2010-05-01
Can you right click the panel and select +Add to Panel > Shutdown?

---

### Post by halfsoul on 2010-05-01
> **wojox said:**
> Can you right click the panel and select +Add to Panel > Shutdown?
Yes, but that give me this icon:
[IMG]http://web.joelishness.mailbolt.com/wrong-power.png[/IMG]
which is just a launcher.  I am looking for this icon:
[IMG]http://web.joelishness.mailbolt.com/right-power.png[/IMG]
which is a menu (if I recall correctly)

---

### Post by conradin on 2010-05-02
Same issue Right here!

---

### Post by spiky001 on 2010-05-02
add indicator applet  (sessions)

---

### Post by conradin on 2010-05-02
Aw, I rebooted and I got it! (solved for me)

---

### Post by halfsoul on 2010-05-02
> **spiky001 said:**
> add indicator applet  (sessions)
That did the trick.  Thank you!!

---

### Post by vinx on 2010-05-16
My button is also missing, but it looks different and it comes back when restarting xorg. If I add it again, I have two of them the next time.

See attachment how it looks. It looks the applet crashed, because it is not redrawn correctly. I cannot move anything to the "empty" place.

Is this a bug I should report?

---

### Post by theodorebook on 2010-05-17
I get the same error - it seems to be some sort of render problem.

---

### Post by pavi_elex on 2010-12-17
Right click on panel--> select add to panel -->select indicator applet session from the list.

---

### Post by jd2012 on 2011-01-31
> **pavi_elex said:**
> Right click on panel--> select add to panel -->select indicator applet session from the list.


This works however, I cant seem to get it to the VERY RIGHT SIDE of the panel i.e top right corner where it was before. I can select 'move' but can only move it so far...

My power button/name disappeared after reboot one day, got an error on the next start up about something missing, do I want to delete the configuration file? I clicked delete not knowing   ](*,)

---

### Post by halfsoul on 2011-02-01
> **spiky001 said:**
> add indicator applet  (sessions)

> **pavi_elex said:**
> Right click on panel--> select add to panel -->select indicator applet session from the list.

> **jd2012 said:**
> This works however, I cant seem to get it to the VERY RIGHT SIDE of the panel i.e top right corner where it was before. I can select 'move' but can only move it so far...
Yes, even though I marked this thread as solved I had the same issue.  I find it unnerving that it doesn't seem possible to restore it to original, but just decided to live with it in the end.

---

