---
title: "how to prevent thunar from autostarting"
date: 2010-09-07
forum: General Help
---

### Post by xiboce on 2010-09-07
I've installed xfce4, compiz, emerald and awn on my ubuntu netbook edition 10.04.

Every time i start a new session and boot into xfce,  thunar automatically opens. However the program is NOT listed under "sessions & start up" nor do i save my sessions everytime i log off, restart or shut down. 

I tried to look for ~/.autostart or ~/.thunar ... to no avail.

Any help on preventing thunar from autostarting everytime would be greatly appreciated.

---

### Post by sisco311 on 2010-09-07
Check out ~/.config/autostart/.

Also try to clear/delete the ~/.cache/sessions/ directory.

---

### Post by aspiredfang on 2010-09-07
most likely, you have a past session being loaded even without the "save session" box ticked. As said, you can clear the session cache or:

- Start up Ubuntu
- Make sure everything is closed and how you want the system to boot
- Restart the computer with the "save sessions" box ticked
- Next time you boot up, before logging off untick that session box again

Voila

---

### Post by xiboce on 2010-09-07
Thank you sisco311 and aspiredfang !!!

There was no sign of thunar under ~/.config/autostart however there was a thunar file under ~/.cache/sessions which I've deleted.

That solved the problem for me. :D

---

