---
title: "Shutdown Applet"
date: 2010-09-23
forum: General Help
---

### Post by Kevopolli on 2010-09-23
I installed ubuntu 10.04.1 on my laptop and after a few problems with the graphics settings I managed to boot up into ubuntu with no problems. Everything was fine for a few days until I started having problems with the shutdown and restart options using indicator applet session, when I used either option from the applet instead of shutting down or restarting it just sent me back to the login screen. I then read on a different forum that the shutdown applet works fine so I added that to the panel and it worked. The problem is that when I logged back in the applet was "greyed out" and was unable to be clicked. I then restarted using terminal only to find that the shutdown applet had disappeared from the panel and it wasn't available to add back to the panel. Does anybody have any idea what happened as I'd like to use it as I have no end of trouble using the indicator-applet-session to shutdown or restart.

Thanks in advance

---

### Post by andrewthomas on 2010-09-23
Reset your gnome-panel to the default

```
rm -r ~/.gconf/apps/panel
```

---

### Post by Kevopolli on 2010-09-26
Sorry for the late reply. Thanks it worked for a few times but now I'm back to the same old problem of ubuntu not shutting down or restarting through the applet. I'll have to investigate further.

---

