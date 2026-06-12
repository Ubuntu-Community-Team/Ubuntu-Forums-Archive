---
title: "Broke my video chip need to uninstall driver"
date: 2011-05-05
forum: General Help
---

### Post by lwatsonz on 2011-05-05
I need help.  I installed a new fan in this computer (thinkipad t60) and in the process somehow broke the video chip or video memory chip.  The new fan is working great so the computer won't overheat now, but I can only use the on-board graphics now.  I was able to uninstall the ATI video adapter in windows 7 from safe mode and get it working, but I don't know how to do the same thing in ubuntu.  I need to uninstall the ATI video driver and install whatever driver is working when you use 'low graphics mode for one session only'.  I will have to make this permanent so ubuntu won't try to reinstall the ATI driver if I upgrade from 10.10 to 11.04 or something.  It's an old computer but might still be of use.  Currently running 10.10.  Any help would be appreciated.

---

### Post by lwatsonz on 2011-05-05
Well I did something even if it was wrong.  I went in to synaptic package manager and removed everything to do with 'ATI'.  Then searched for 'generic video driver' in synaptic and installed the one it found.  xserver-xorg-video-v4l is what it was called. I don't know if there is a better one for my purpose or if this will be permanent, but I can boot in to ubuntu normally with crashing right away now.   :)  I didn't even have to use the terminal window or sudo.

---

