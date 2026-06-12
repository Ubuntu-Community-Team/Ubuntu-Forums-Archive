---
title: "Show-desktop icon, but not a plasmoid..."
date: 2009-07-30
forum: General Help
---

### Post by NåttKooltNamn on 2009-07-30
Howdy folks!
Long time listener, first time caller...:)
I'm on a Jaunty Kubuntu system, just made the clean install, the HD on my previous (Hardy) just gave up. So far I'm about fifty-fifty on this whole KDE4 thing.
Anyway, what I want to know is how I can make a show-desktop-icon (minimize all windows) in my quicklaunch-plasmoid. I don't want the "stand alone" plasmoid due to the waste of screen realestate (this is one of my gripes with KDE4 btw, everything is so freaking huge). I seem to remember doing something like this on an earlier system with a .desktop file...
Thankfull for all help, tips and pointers!
/Dave

---

### Post by Zorael on 2009-07-30
I browsed the available dbus calls, but I couldn't find anything resembling "show desktop". There is a "cascade windows" and a "unclutter windows" call, but nothing else in lieu of window manipulation. That would otherwise have been an option; to create a script that sends such a call.

My current solution is to put a Show Desktop widget *on* the desktop, then bind a shortcut to (the Windows default) meta+d. That way it isn't spending my precious screen budget, while still being there for using.

*edit:* From #kde@freenode:
> [01:09] <aseigo> zorael_: you want to toggle the show desktop? we don't have dbus call for that (yet).. we're probably getting full dbus access to runtime plasma components, however, in 4.4

---

### Post by NåttKooltNamn on 2009-08-01
Thanks, that is indeed a good solution. Actually it might even be better than the icon...

---

