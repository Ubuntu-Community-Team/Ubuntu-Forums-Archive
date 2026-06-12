---
title: "OpenGL drawing shifted window directions in Kubuntu 11.10"
date: 2011-12-13
forum: General Help
---

### Post by kooldino on 2011-12-13
Long story short:

If I run Desktop Effects compositing and use OpenGL rendering, I get an odd shifted title bar and window decorations.  If I switch the compositing type to XRender, everything renders properly (albeit, very slowly).

My guess on how to fix this (and be able to run OpenGL compositing) would be to find an older driver and install that.

I'm running an old Nvidia card - an AGP GeForce MX420, iirc.

---

### Post by gyurma on 2011-12-14
I have same problem with freshly installed and updated kubuntu 11.10.

 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

when switching to xrender everything is ok.

The problem seems to be a setting at the user settings, because I first used old (other, sidux) settings, and there there were no problems. Only after playing with switching to xrender and then back to OpenGL this appeared. 
A freshly added user gets also this strange window look...

---

### Post by kooldino on 2011-12-15
What user settings do you suggest are the culprit?

---

### Post by kooldino on 2011-12-19
Bump

---

### Post by gregthomas on 2012-04-28
I also have this problem, the only way I can straighten this up is to turn off desktop effects.  Has anyone found a fix for this? I have this on 2 different computers one has the agp mx420 graphics card and the other one is an integrated Intel 865g so I don't think it's nvidia related. However both are IBMs and both have the 865g integrated graphics, I'm just using the nvidia card on one.

---

