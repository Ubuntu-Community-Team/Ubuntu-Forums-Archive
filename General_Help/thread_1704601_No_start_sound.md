---
title: "No start sound"
date: 2011-03-10
forum: General Help
---

### Post by Julian Luna on 2011-03-10
Hello all!
Well I did exactly this
[http://www.jeffsplace.net/node/12](http://www.jeffsplace.net/node/12)
And now I can hear very well the sound
But now my ubuntu startup welcome sound doesn't play. What's the little fix I need?
Thanks

---

### Post by Hedgehog1 on 2011-03-10
Menu to System >> Preferences >> Startup applications

[IMG]http://img825.imageshack.us/img825/2311/startupsoundsetting.png[/IMG]

Click/Unclick 'Gnome Login Sound'.

I don't know if it uses/used pulseaudio.

***The Hedge***

:KS

---

### Post by Julian Luna on 2011-03-11
Bro I just tried it but it didn't work at all

---

### Post by Hedgehog1 on 2011-03-12
Well darn.

It was **SUCH** a good idea.  *It was even a nice picture, too.*

I am out of ideas; Perhaps another forum member can suggest how to get the login sound to play when pulse audio has been removed?

***The Hedge***

:KS

---

### Post by Julian Luna on 2011-03-12
=( Very much thanks bro you tried it :] Im gratefull
Anyone got any idea? I'm using ALSA

---

### Post by Julian Luna on 2011-03-15
bump

---

### Post by Krytarik on 2011-03-15
Check in "System -> Preferences -> Sound" if "Sound Effects" are not muted and a "Sound theme" is chosen, "Ubuntu" is the default.

---

### Post by Julian Luna on 2011-03-21
Thanks but when I do this it keeps saying "Waiting for sound system to respond"

---

### Post by Krytarik on 2011-03-21
Just a wild guess, how about disabling this option in "gconf-editor"?: "/desktop/gnome/sound/enable_esd".

---

