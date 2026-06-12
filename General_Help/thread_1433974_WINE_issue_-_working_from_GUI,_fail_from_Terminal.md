---
title: "WINE issue - working from GUI, fail from Terminal"
date: 2010-03-19
forum: General Help
---

### Post by Chesamo on 2010-03-19
I'm running a game called EV Nova (which runs perfectly well in WINE). I'm trying to set up a Menu item for it, but the Terminal command fails.

**What works:**
Right-clicking EV Nova.exe and selecting "Run with Wine Windows Program Loader"

**What doesn't:**
wine /home/user/.wine/drive_c/Program\ Files/nova/EV\ Nova.exe
wine "/home/user/.wine/drive_c/Program Files/nova/EV Nova.exe"
wine "C:\\Program Files\\nova\\EV Nova.exe"

...or pretty much any other Terminal command. Help?

---

### Post by anoop999 on 2010-03-19
Try:

env WINEPREFIX="/home/**USERNAME**/.wine" wine "C:\Program Files\**PROGRAM**_**PATH**" 

replacing **USERNAME **with your username and**PROGRAM**_**PATH **with the path to the Windows program[B].
[/B]

---

### Post by Chesamo on 2010-03-19
Done; no effect.

---

### Post by Chesamo on 2010-03-21
*sigh* Bump... is there something different about the right-click commands that I'm not aware of?

---

### Post by Chesamo on 2010-03-24
Figured it out... Have to use```
wine start /Unix ~/.wine/drive_c/Program\ Files/nova/EV\ Nova.exe
```to get it working. In case anyone's interested...

---

