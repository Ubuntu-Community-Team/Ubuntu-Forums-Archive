---
title: "The new NVIDIA drivers in Lucid and Maverick mess up splash"
date: 2010-10-05
forum: General Help
---

### Post by madmax.santana on 2010-10-05
**Prologue:**
The new NVIDIA drivers don't seem to work as seamlessly as back in Jaunty and before.
In Lucid when I activated the drivers I had to do some grub tweaks to make my splash look normal... But with Maverick it is even more messed up... 

**Problem:**
The splash either doesn't appear at all (black screen) or it appears in the text format rather than graphics... In some instances it even hopelessly tried to load the graphics splash - loaded the background but the instead of Ubuntu logo and the progress-bar animation it displayed a "Ubuntu 10.10" in a monospace font.

**Self-Diagnosis:**
I know I shall again have to do the grub tweaks. I have applied the same tweaks as of Maverick but that rendered my system inoperable and I had to do a fresh installation. I have no idea what to do on Maverick and Google is no help as such, probably because Maverick is new and fewer people have asked questions about it before me.

[COLOR="Navy"]Edit[/COLOR]: [This is my own post]("http://ubuntuforums.org/showthread.php?t=1552261") while with Lucid... I tried this with Maverick and the grub resolution seems fine, but after grub, the resolution of splash and tty is horribly low, maybe 320x240... I can't post the images here but you can imagine by the fact that the one letter is almost 1'' high and 0.75'' wide. Also in splash the Ubuntu logo takes up the whole screen...

**Required:**
If any expert could show me around on the feature and help me make it work, I shall be really obliged.

---

### Post by efflandt on 2010-10-05
Lucid and Maverick do not really use "splash", they use something call "plymouth", although, they still use the **splash** kernel boot parameter.

What video card do you have and which nvidia drivers are you using?  Did you install both systems from scratch or upgrade an earlier Ubuntu version?

Both activated using Hardware Drivers work fine for me with relatively new GT 220, except that the screen is somewhat shrunken in Lucid on a 1080p DVI to HDMI display, until the gui login comes up full screen (and X is full screen 1920x1080).  In Maverick even Ubuntu with the dots is full screen for me.

Have you tried deactivating and re-activating the video drivers?  I noticed that when I recently upgraded one system from 9.10 to 10.04 (default video drivers) that flash did not show up in Firefox even though flashplugin-installer appeared to be installed.  And ubuntu-restricted-extras showed as not installed.  Even after installing the restricted-extras which include flash, it still was not there until I selected reinstall for flashplugin-installer.  So maybe something similar happens for proprietary video drivers (not quite right) when upgrading Ubuntu versions.

---

