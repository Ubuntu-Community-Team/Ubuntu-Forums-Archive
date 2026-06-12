---
title: "Unble to re-enable ctrl+alt+backspace"
date: 2009-07-28
forum: General Help
---

### Post by andresmh on 2009-07-28
I am trying to enable ctrl+alt+backspace to restart Xorg but I am not able to do it. In my/etc/X11/xorg.conf I have

```
Section "ServerFlags"
        Option  "DontZap"       "False"
EndSection
```

I also tried installing some package that supposedly would do it but no luck.

What am I missing?

I'm on Karmic

---

### Post by chrisinspace on 2009-07-28
I don't know about Karmic, but this worked for me in Jaunty:

[http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html](http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html)

---

### Post by DaithiF on 2009-07-28
Hi, just checking -- have you restarted X since making the change ?  It won't re-load its config on the fly, so any changes need a restart to take effect.

---

### Post by wojox on 2009-07-28
Section "ServerFlags"
        Option          "DontZap"               "false"
EndSection

Then re-start computer.

---

### Post by philinux on 2009-07-28
> **andresmh said:**
> I am trying to enable ctrl+alt+backspace to restart Xorg but I am not able to do it. In my/etc/X11/xorg.conf I have

```
Section "ServerFlags"
        Option  "DontZap"       "False"
EndSection
```I also tried installing some package that supposedly would do it but no luck.

What am I missing?

I'm on Karmic

You can use this any time.
Alt + SysRq + k

The k kills the x session and takes you to the login screen.

---

