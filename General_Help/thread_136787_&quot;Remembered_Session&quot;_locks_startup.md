---
title: "&quot;Remembered Session&quot; locks startup"
date: 2006-02-26
forum: General Help
---

### Post by Mazin on 2006-02-26
When I'm logging in to KDE, it'll get to the Restoring Previous Section part, and will stop at a certain percentage and just freeze.  I can force X to restart, but logging in just freezes again.  Is there a way from failsafe or something to wipe the previous session so the trouble-causing app (or whatever it is) won't automatically start?

---

### Post by Xian on 2006-02-26
Check the contents of your /home/username/.kde/Autostart directory.

---

### Post by pestilence4hr on 2006-02-26
Maybe it's in ~/.kde/Autostart ?  Try removing what's in there.

---

### Post by Mazin on 2006-02-26
Isn't ~/.kde/Autostart and /home/username/.kde/Autostart the same?

Anyways, I looked in .kde/Autostart, and the only thing in there was a .directory file giving a lot of translations for the word Autostart.  I'm still having the problem of the restore session process locking up.  Any other way to wipe it?

---

### Post by aysiu on 2006-02-26
You could try Control-Alt-F1
Log in
Then ```
rm ~/.kde/share/config/session/kwin*
```

---

### Post by pestilence4hr on 2006-02-26
[QUOTE=Mazin]Isn't ~/.kde/Autostart and /home/username/.kde/Autostart the same?
[/QUOTE]

Yes.  Xian and I replied @ the same time.

---

