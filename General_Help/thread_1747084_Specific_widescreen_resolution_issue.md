---
title: "Specific widescreen resolution issue"
date: 2011-05-02
forum: General Help
---

### Post by DoktorSeven on 2011-05-02
Issue: 
For my 16:9 LG widescreen monitor -- native resolution 1920x1080, which *is* working -- the secondary widescreen resolution, 1280x720, is coming up incorrectly.

Using Kubuntu 11.04 with fglrx (however, see below) -- issue also occurs on other desktops (Gnome, XFCE4, fluxbox), the previous version of Ubuntu (10.10), and Slackware.  Video is onboard Radeon 3200HD.

Specifics:
If I choose or have a program set the resolution of 1280x720, the screen changes into a "windowed" mode where there are large black borders surrounding a "widescreen" display in the middle.  This is not simply a matter of edge adjustment; these are very large borders.

The issue is that my monitors OSD while in this mode displays the resolution as 1280x960.  I believe the incorrect mode is being sent to the monitor while X still attempts to display the geometry correctly, thus giving me a "widescreen" mode with black bars within an actual 4:3 mode on my monitor, thus giving me black bars on both the sides and top/bottom.  There seems to be no specific errors or issues mentioned in Xorg.0.log during resolution switch regarding this.

If I disable fglrx, this issue persists; however, I am able to add a modeline to xorg.conf to override this issue and regain the proper widescreen mode at this resolution.  It seems, though, that fglrx ignores modelines and thus this will not work while I have the fglrx driver installed, and given I use this resolution for fullscreen gaming, keeping the fglrx driver installed would be preferable.

This issue also existed in the previous version of Ubuntu (10.10), as well as Slackware 13.1 (have not tried the latest version of Slackware).

This issue does *not* occur in Microsoft Windows Vista or 7, even with the generic video drivers -- when changing to 1280x720, the display is correct and the monitor OSD correctly gives the resolution as 1280x720.

Mostly wondering if anyone else has this specific issue so I can go forward with trying to get it resolved.

---

### Post by DoktorSeven on 2011-05-05
Pulling this up again to see if anyone has seen anything like this.  I'm pretty much convinced it's an X issue, combined with fglrx unable to use modelines, so probably should file a bug report of some type unless one already exists (nothing precisely like this does from what I've seen).

---

