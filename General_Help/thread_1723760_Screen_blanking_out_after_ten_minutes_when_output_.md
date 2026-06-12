---
title: "Screen blanking out after ten minutes when output to TV over S-Video..."
date: 2011-04-07
forum: General Help
---

### Post by icebox83 on 2011-04-07
New Linux user here. I'm running Ubuntu 10.10 w/ an ATI HD 4350 and trying to output to a CRT television over S-Video @ 640x480. Problem is the screen blanks out after ten minutes no matter how I configure my screensaver or power management settings. I've done some research regarding commands in Terminal, but I can't find anything straightforward. Any suggestions?

---

### Post by icebox83 on 2011-04-07
Nobody?

---

### Post by f1tz on 2011-04-07
Not a fix, but try:[INDENT]*xset s off* --This will allow you to turn the screen saver off
[/INDENT][INDENT]*xset -dpms* --This will disable the Energy Star features
[/INDENT][INDENT]*xset q* --will show you the current settings.
[/INDENT]These get reset to defaults when you log off, so, if it works for you, have them set on login if you like.

You could also try editing xorg.conf, add the line to the ServerFlags section:

[I]Section "ServerFlags"
    Option      "BlankTime"     "60"
EndSection[/I]

Which should set the screen blank timeout to 1hr. If it still does it, you may need to change the *"StandbyTime"*, *"SuspendTime"*, or *"OffTime"* options in a similar manner. You may also need to disable the "Display power management", easiest way is through the GUI in system settings.

---

### Post by Schuby007 on 2012-02-20
Just a supplement on the previous reply...

Appending "xset s off" to the bottom of my .profile file in my home directory fixed the issue for me. Effectively it completely disables the screensaver every time I log in xD

---

