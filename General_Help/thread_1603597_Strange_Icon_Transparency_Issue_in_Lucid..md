---
title: "Strange Icon Transparency Issue in Lucid."
date: 2010-10-22
forum: General Help
---

### Post by AlphaMack on 2010-10-22
I'm at a friend's Ubuntu desktop running Lucid and noticed something strange with the icons.  With the default Ambiance/Radiance and several other themes, I noticed that the icons appear jagged and are missing the inactive transparency.  Oddly enough, the icons appear normal when the Dust theme is selected.  You can see this in the screenshots attached.

I can replicate this issue systemwide, even under a guest account.  The graphic card on this box is Intel integrated.  I happen to have a live CD of Lucid and it does NOT exhibit this issue.  Perhaps a configuration file is messed up somewhere?

Any ideas?

---

### Post by dcstar on 2010-10-23
> **AlphaMack said:**
> I'm at a friend's Ubuntu desktop running Lucid and noticed something strange with the icons.  With the default Ambiance/Radiance and several other themes, I noticed that the icons appear jagged and are missing the inactive transparency.  Oddly enough, the icons appear normal when the Dust theme is selected.  You can see this in the screenshots attached.

I can replicate this issue systemwide, even under a guest account.  The graphic card on this box is Intel integrated.  I happen to have a live CD of Lucid and it does NOT exhibit this issue.  Perhaps a configuration file is messed up somewhere?

Any ideas?

Some themes may use high colour depth icons and others may not. If you have video hardware that does not good native Linux support (like Intel, apparently) then the system may be running in low-res video mode and the hi-res icons may then look bad.

---

### Post by AlphaMack on 2010-10-24
Ah that would explain it then.  I'll look more into the video support on this box.  Thanks.

---

### Post by AlphaMack on 2010-11-02
A follow up to this thread:

I traced the issue to the version of xserver-xorg-video-intel supplied by the ubuntu-x-swat PPA for Lucid.  Rolling back to the original Lucid package resolves this.  This may be specific to the chipset because I personally have this PPA installed on my Lucid machine and do not experience this.

---

