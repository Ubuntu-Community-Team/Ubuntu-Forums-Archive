---
title: "Enter key makes gnome crash/logout after bootup"
date: 2011-12-29
forum: General Help
---

### Post by 00000 on 2011-12-29
After I boot up my laptop into Gnome, the very first time I hit the enter key causes Gnome to crash and I'm immediately put back at the login screen.  All programs I'm running are killed.  After I log in again a second time, the problem doesn't happen again.  It always happens exactly once after I boot up my machine.

This is *extremely* annoying, and seems like such a stupid bug...  I couldn't find an answer.  I don't know if it's Gnome...  I assume if Gnome exits and puts me back at the login screen it must be some Gnome issue.  Does anyone have a clue?

I'm running Oneiric on a MacBook Pro 8,3 laptop and using Gnome Shell (the same problem happens when I use the Gnome Panels).

---

### Post by matt_symes on 2011-12-30
Hi

> Does anyone have a clue?


Absolutely no idea :)

The first thing i would check are your log files though.

Have a look in

```
/var/log/Xorg.0.log
```

and 
```

~/.xsession-errors
```

They may provide some clues as to what is happening. Post them back here if you want to. Try to just post the part of the logs around the time of the crash.

Kind regards

---

### Post by 00000 on 2011-12-31
I think I fixed it...  I downgraded the version of the ATI Catalyst driver I was using (from the new 11.12 version down to 11.11) and now the bug is gone (so far).  I'm not sure why the enter key would cause this or what Gnome is trying to do when I push it.

I forgot if I mentioned this in the other post, but I'm using a MacBook Pro 8,3...  So anyone else with this model might want to avoid the ATI 11.12 driver.

---

