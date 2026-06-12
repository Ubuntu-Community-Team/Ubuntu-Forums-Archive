---
title: "how to use mplayer plug-in in chrome"
date: 2009-10-15
forum: General Help
---

### Post by banana jama on 2009-10-15
i've just downloaded the alpha version of chrome browser. i like it alot but the only thing is i can't figure out how to get the mplayer plugin working. does anyone know how to do this?

---

### Post by DotNate on 2009-10-15
I seem to recall reading that the linux version of google chrome has very limited support for plugins right now.

---

### Post by banana jama on 2009-10-15
yeah i found a way to post my flash plugin to chrome but i cant seem to get the same method to work for the mplayer plugin.

---

### Post by banana jama on 2009-10-16
ok i've been doing some research and i've solved the problem. the totem plug-in takes precedence over mplayer's plug-in so to get mplayer working just delete the totem plug-in using:

> sudo aptitude remove totem-mozilla

---

### Post by yama-chan on 2011-03-12
I also have same problem (couldn't hear mp3 in chrome browser),
so plugin [tiny mp3 player]("https://chrome.google.com/webstore/detail/klphnalhafkamjdgcmpmijohkkokajbg") but couldn't sound.

I did comand below, but couldn't solve the problem.
 >sudo aptitude remove totem-mozilla

---

