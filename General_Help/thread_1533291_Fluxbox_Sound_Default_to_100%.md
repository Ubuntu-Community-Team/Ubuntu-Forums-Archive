---
title: "Fluxbox Sound Default to 100%"
date: 2010-07-17
forum: General Help
---

### Post by rizlmilk on 2010-07-17
Is there a way to default volume to 100% in the terminal with gnome-volume-control-applet or any other program? I am setting up a dedicated Zsnes machine which boots into Fluxbox but the volume is muted by default. There isn't a man page for gnome-volume-control-applet.

When I log into Gnome the volume is set to 100%, but Fluxbox is always set to mute.

---

### Post by rizlmilk on 2010-07-20
I've tried playing with amixer with no success. The command I used is "amixer sset Master 70%". This command does work, but only in alsamixer. The command changes the volume in alsamixer to 70%, but still no sound plays because gnome-volume-control-applet is still set to mute.

I keep looking everywhere trying to find a way to pass command line arguments through gnome-volume-control-applet with no luck.

---

