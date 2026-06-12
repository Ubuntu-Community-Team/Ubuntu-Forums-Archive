---
title: "Upper right corner shut down button went missing!"
date: 2010-11-09
forum: General Help
---

### Post by in.trouble on 2010-11-09
Hello.

I have found a bug. Sometimes the shut down and log out menu button is missing from the upper right corner and i have to shut down via terminal or create the shut down button to the panel.

see where the arrow points at:

[IMG]http://i54.tinypic.com/igzvo2.png[/IMG]

I had this problem before format too.

---

### Post by alphaamanitin on 2010-11-09
I have had this bug before as well.  Never was able to find any cause, but usually manually adding the button back solved the problem for months. I was running 9.10 @ the time.

AlphaA

---

### Post by karthick87 on 2010-11-09
> **in.trouble said:**
> Hello.

I have found a bug. Sometimes the shut down and log out menu button is missing from the upper right corner and i have to shut down via terminal or create the shut down button to the panel.

see where the arrow points at:

[IMG]http://i54.tinypic.com/igzvo2.png[/IMG]

I had this problem before format too.

What version of ubuntu you are running?Let me a file a bug report on this.

---

### Post by yiannis66 on 2010-11-09
It's also happens to me lots of times ,everytime I manualy put it back and after a restart everythink is fine.

---

### Post by pqwoerituytrueiwoq on 2010-11-09
reload the panels
```
killall gnome-panel
```

---

### Post by ajgreeny on 2010-11-09
You may have removed or lost the "indicator-applet-session" from the panel, so right click somewhere in an empty part, and add it back.

You can also add the "shutdown" button if you only have one user, and prefer it.

---

### Post by alphaamanitin on 2010-11-09
> **ajgreeny said:**
> You may have removed or lost the "indicator-applet-session" from the panel, so right click somewhere in an empty part, and add it back.

You can also add the "shutdown" button if you only have one user, and prefer it.
I know in my case I did neither of those.  I did mess with any of the panel settings and one day when I booted up 9.10 it was simply gone.  Adding it back manual fixed the issue but a few months later it happened again.  I have not experienced this with 10.04, yet.

AlphaA

---

### Post by in.trouble on 2010-11-09
I have had this bug in older Ubuntu versions aswell, but atm I am using 10.10

After I restart the computer, everything is fine.

Normally it looks like this:

[IMG]http://i54.tinypic.com/4l0lrb.png[/IMG]

getyourkarthick, how can i help you file the report? I would be glad to help.

And pqwoerituytrueiwoq, thanks for this command:

```
killall gnome-panel
```

---

### Post by lisati on 2010-11-09
Go for it, team! I occasionally have a similar problem on my laptop (currently running 10.04), but haven't bothered looking into it; tapping on the power button and then restarting via the popup menu usually seems to bring it back.

---

### Post by alphaamanitin on 2010-11-09
Hmm.  For me rebooting never worked.  I never tried killing the gnome panel though.

AlphaA

---

### Post by mdsmedia on 2011-02-28
I just upgraded from Lucid to Maverick and had the power button disappear (not appear) after upgrade.

Killing the panel fixed it, but it has happened before...probably after last upgrade. Last time I added the button to the panel manually. Maybe killing it would have worked that time too.

---

