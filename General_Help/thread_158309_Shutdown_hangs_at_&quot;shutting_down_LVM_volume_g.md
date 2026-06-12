---
title: "Shutdown hangs at &quot;shutting down LVM volume groups&quot;"
date: 2006-04-10
forum: General Help
---

### Post by mattotoole on 2006-04-10
I'm running Breezy on an IBM T20 laptop.  When I try to shut down from the Gnome System|Logout menu, my system hangs at "shutting down LVM volume groups."  Sometimes this only lasts several minutes, but most of the time it's indefinite, as in overnight.  I can't always wait so I power off, with no apparent ill effects.  Sometimes it seems Evolution's settings were not saved.  What's causing this, and how do I fix it?  BTW, I have no extra devices attached, USB or anything else.

---

### Post by dcstar on 2006-04-11
[QUOTE=mattotoole]I'm running Breezy on an IBM T20 laptop.  When I try to shut down from the Gnome System|Logout menu, my system hangs at "shutting down LVM volume groups."  Sometimes this only lasts several minutes, but most of the time it's indefinite, as in overnight.  I can't always wait so I power off, with no apparent ill effects.  Sometimes it seems Evolution's settings were not saved.  What's causing this, and how do I fix it?  BTW, I have no extra devices attached, USB or anything else.[/QUOTE]
Possibly that is just masking what actually is causing the problem.

If you edit /etc/default/rcS to have:
```
VERBOSE=yes
```
then you may get more information to help identify the problem further.

---

### Post by mattotoole on 2006-04-11
[QUOTE=dcstar]Possibly that is just masking what actually is causing the problem.

If you edit /etc/default/rcS to have:
```
VERBOSE=yes
```
then you may get more information to help identify the problem further.[/QUOTE]

I tried that, and got "No LVM volumes found."  This time it shut down as it should though.

So it's looking for something but not finding it, when it won't shutdown normally?

---

### Post by dcstar on 2006-04-11
[QUOTE=mattotoole]I tried that, and got "No LVM volumes found."  This time it shut down as it should though.

So it's looking for something but not finding it, when it won't shutdown normally?[/QUOTE]
Possibly, it could be some process crashed or there is a hardware issue that is hanging the machine - could be tough to pinpoint.

---

