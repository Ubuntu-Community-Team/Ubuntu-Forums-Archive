---
title: "Multi Monitor ( 3 displays ) with ATI Radeon on LXDE"
date: 2012-05-22
forum: General Help
---

### Post by RubenRybnik on 2012-05-22
Running Lubuntu 12.04, I've successfully installed the ATI drivers from the repo( proprietary ATI/AMD normal version, not post-release ) and have 3 monitors working as one display which I setup in Catalyst Control Center.  NOTE: Xinerama is not enabled, just one huge desktop, not 3 separate ones.

Everything is working pretty well, however I have a couple small, but annoying issues wondering if someone could help out.

1.) The Taskbar/Panel is spread across all 3 monitors, makes sense since LXDE thinks it's one display. However I'd like to get the Panel setup to display only on the middle monitor, and windows to launch on the middle monitor by default.  It would be nice if I could have 3 separate panels, one for each monitor with it's own window list.  But this isn't 100% necessary.

2.) This may be a hardware issue, but my 2 side monitors are 3" smaller than my middle one physically. Not sure if that's the problem here, just noting it.  But the two side displays are smaller than the screen and show about a 2" black border around the desktop, and it doesn't size to fit the monitor.  Usually this can be solved with an overscan setting but didn't see one in the ATI Control Center.

That's really the only issues I'm having for now, all in all it was an easy setup( much easier than compiling modules, manually editing X11 config, etc.. like a couple years back )

EDIT: Ok, panel issue pretty much solved by sizing to 1920x1080 and setting to center, suppose I could just add 2 more for the other monitors if I wanted.  However still having the desktop scaling issue.

---

