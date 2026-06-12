---
title: "Minicom Window resets to 80 Columns in 9.04?"
date: 2009-07-01
forum: General Help
---

### Post by cdub3030 on 2009-07-01
Since upgrading to 9.04 when I attempt to make my minicom window wider than 80 columns it resets to 80 and will not go any wider.  I did not have this problem with previous versions of ubuntu.  It is very annoying as I am constantly using minicom for serial port access to routers/switches.  Anyone found a fix for this?

---

### Post by cdub3030 on 2009-07-02
Although I still have not found a resolution to the minicom issue, I did come across a good replacement named picocom. Picocom runs in the existing terminal window it is initiated from and conforms to whatever size the window is set to.

'aptitude install picocom'

---

### Post by The Cog on 2009-07-02
You might also be interested in the existence of package gtkterm.

---

### Post by HermanAB on 2009-07-02
Cutecom is probably the best.  Since discovering that one, I don't use minicom anymore.

---

### Post by cdub3030 on 2009-07-02
> **The Cog said:**
> You might also be interested in the existence of package gtkterm.

tried gtkterm before picocom, didn't like it for a few reasons:
 - No scroll back
 - Wouldn't save default color/font settings (don't like white on black much)

---

### Post by cdub3030 on 2009-08-25
see [http://ubuntuforums.org/showthread.php?t=1194600](http://ubuntuforums.org/showthread.php?t=1194600) for fix

---

