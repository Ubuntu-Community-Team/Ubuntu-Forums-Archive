---
title: "Change Pidgin status when screen locks."
date: 2010-05-31
forum: General Help
---

### Post by artursm on 2010-05-31
Hi, does anyone know of a way to automatically set my pidgin status to "away" as soon as I lock the screen? I always lock the screen when leaving my office, and it'd be nice if pidgin would automatically mark me as "away".

If there's a command to change pidgin status, that would probably do the trick, since I can then bind this command along with the "lock screen" command to ctrl+alt+L.

Any other way you can think of is welcome. I know I can set pidgin to mark as away if I don't touch anything in X minutes, but I'll sometimes work for 20 or 30 minutes without touching the mouse or keyboard, and I don't want it marking me as away 'cause I'm still right in front of the machine.

If I wasn't clear enough, please ask.

Running Ubuntu 10.04 Lucid Lynx

---

### Post by Ankur Dave on 2010-06-21
The [Away-on-lock plugin]("http://costela.net/projects/awayonlock/") for Pidgin works for me. It's in the Ubuntu repositories as "pidgin-awayonlock", so run the following command in Terminal to install it:

```
sudo aptitude install pidgin-awayonlock
```

The plugin should show up as "Away-on-lock" in Pidgin's "Plugins" window. Once you enable it, Pidgin should start changing to your default away status as soon as you lock the screen.

Hope that helps!

---

