---
title: "system monitor window is fuzzy and all lines"
date: 2010-04-28
forum: General Help
---

### Post by mtp337 on 2010-04-28
Hi Folks,

I have an old windows Small biz server that has been decomissioned and I have been dying to try ubuntu 9.10.  I loaded the desktop version on this box:

PowerEdge 1800
graphix card:
Radeon RV100 QY [Radeon 7000/VE]

Everything looks great, but the system monitor window is all lines and fuzz.  I don't even know where to start looking for a fix.  Anyone have any clues?

Thanks in advance...

---

### Post by utnubuuser on 2010-04-28
Follow this thread:[http://ubuntuforums.org/showthread.php?t=246746&highlight=thinkpad+x31+ati+M6]("http://ubuntuforums.org/showthread.php?t=246746&highlight=thinkpad+x31+ati+M6")

The thread is about the thinkpads with ati cards - driver corresponds to the same ati driver as would be used in your little machine.


The solution is probably as easy as switching off/on Rendering.
ie:

 Option "RenderAccel" "off"

---

### Post by mtp337 on 2010-04-28
thanks for the lead.  looks like folks are editing a x11.config file to get past this.  before i create an x11.config file since i don't seem to have one....  it there a simple way to turn of the rendering with out creating one from scratch

---

