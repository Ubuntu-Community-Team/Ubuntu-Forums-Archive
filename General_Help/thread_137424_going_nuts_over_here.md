---
title: "going nuts over here"
date: 2006-02-27
forum: General Help
---

### Post by ingriffiths on 2006-02-27
ok, apparently a program other than xmms is blocking my sound card...or maybe it's even xmms itself...
either way, i can't get ANY sounds to play right now and it's annoying
i can't find anything in forum searches...
if someone could give me an idea or point me to a good thread i'd appreciate it

---

### Post by DOtSlaSHuCantCME on 2006-02-28
[QUOTE=ingriffiths]ok, apparently a program other than xmms is blocking my sound card...or maybe it's even xmms itself...
either way, i can't get ANY sounds to play right now and it's annoying
i can't find anything in forum searches...
if someone could give me an idea or point me to a good thread i'd appreciate it[/QUOTE]


System Monitor \\:D/    might be xine:-k .

---

### Post by K.Mandla on 2006-02-28
If you can't pick it out with the System Monitor (Applications > System Tools > System Monitor), you might try a reboot. If it's still preoccupied after a clean reboot, then there's something strange going on.

---

### Post by DaMasta on 2006-02-28
Xmms cannot play or cannot play mp3s? If it's the latter, you need the gstreamer-xine package and changed your media system accordingly.

---

### Post by newuser111 on 2006-02-28
try sudo killall esd in a terminal and see if xmms can play mp3s, esd is the sound daemon for gnome but it interferes with other sound output, or you can change the xmms output in options to a different plugin, even esd, but i recommend alsa

afaik, xmms can play mp3s out of the box, unlike rhytmbox which needs gstreamer plugins

---

### Post by ESM on 2006-02-28
A bit OT but thanks for pointing me towards the system monitor too. I am using Ubunbtu for a few days now and didn't see that yet. But unbelievable: 0 cpu use mostly while working. That's quite different in WinXP ;)

---

