---
title: "Unmute my computer from command line after starting computer muted?"
date: 2011-01-08
forum: General Help
---

### Post by duckwars on 2011-01-08
I have an Asus 1005PE that I'm using Ubuntu 10.04 on.  I've set up a hot key to mute/unmute by using the command

amixer sset Master toggle

For some reason it works fine if the computer is booted while not being muted, but if the computer is booted and is muted, the command will not unmute.

Any ideas?

---

### Post by BbUiDgZ on 2011-01-08
this is a guess

if your toggle is to "mute" then "unmute" its going to fail if the computer is already "muted" as its going to want to "mute" first rather than "unmute"

---

### Post by mc4man on 2011-01-08
It should (and does) work fine as long as you don't mute thru the sound preferences applet. In that case amixer can't unmute

---

