---
title: "Fullscreen *.mov in Mplayer plays slowly."
date: 2006-04-25
forum: General Help
---

### Post by BitTorrentBuddha on 2006-04-25
Hi, I have changed the mplayer config to read zoom=yes I have also set the default driver to xv, the files display at fullscreen size, but they slowdown to about .75 normal speed and the audio plays at a normal rate. I have onboard video and a cheap sound card (PCI). Could the problem lie in the fact that my onboard video can't handle the zoom? (Fullscreen works perfectly in totem, but I use the mplayer plugin for firefox.)

---

### Post by cilynx on 2006-04-25
Not sure if this is your only problem, but "zoom=yes" enables software scaling for systems that don't support hardware scaling.  If you're using software scaling, fullscreen is going to be dog slow.  If you're effectively using "vo=xv", then you don't need the zoom line and hardware scaling should do it's thing at full speed.

---

### Post by paritybit on 2006-04-25
Also from memory .mov/quicktime movies are really slow at times and will bash your system around a bit. Might just be that mplayer doesn't really handle the format that well. I am thinking that it is closed standard format and they had to hack something together to play it?

---

