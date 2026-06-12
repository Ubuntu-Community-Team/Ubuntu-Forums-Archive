---
title: "Problems with Extended Desktop (Dual Monitor) on KDE"
date: 2010-09-02
forum: General Help
---

### Post by dborba on 2010-09-02
System Config:
Running Ubuntu 10.04 on Lenovo X60 tablet & a Samsung SyncMaster203b. 
KDE installed by adding the kde-full package through synaptic.

Having issues setting up an extended monitor on KDE. The problem seems to occur when the two screens are set to different resolutions (it works fine while both screens are in the laptop's native 1024x768.) However, when I increase the resolution of the external monitor X crashes on me. This is not a problem in gnome however, where the extended desktop has been working fine.

There seems to be a couple lines pop up on top of the screen on a console before the crash, but I haven't been able to read or find them. The only thing that looked suspicious is a seg fault on Xorg.0.log.old.

I tried setting the monitors up on the console using xrandr so I could try to redirect stdout and stderr to files & see possible problems, but no luck. Any ideas?

---

### Post by dborba on 2010-10-10
Thought I might bump this up since it's been a while & I've got no replies. I've been using gnome where there is no problem, but I miss KDE so it would be nice to get it fixed.

---

