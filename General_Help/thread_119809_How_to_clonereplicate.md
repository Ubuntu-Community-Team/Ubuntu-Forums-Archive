---
title: "How to clone/replicate?"
date: 2006-01-20
forum: General Help
---

### Post by SuperMike on 2006-01-20
I have a tool that permits me to clone or replicate PCs, sector by sector. It's called Symantec Ghost. Many of you may be familiar with it. Anyway, I'm having trouble replicating an Ubuntu 5.10 system to another identical system. These are IBM kiosks model number 4835-152. When we clone it, I can see the image on the Ghost server and can expand the folders, so I know at least the image is intact. But when we clone this from the Ghost server down to another kiosk, and then reboot, it boots up and says this, but does nothing else -- it's hung:

GRUB
_

Anyone have an idea why this might be hung? We tried more kiosks and haven't found the cause.

If this cannot be figured out, then perhaps you can tell me another way to replicate one Ubuntu system with another system.

---

### Post by jstueve on 2006-01-20
Is the /boot directory in the image?  

*spitballing*

---

### Post by Ocxic on 2006-01-20
will ghost support the ext3 filesystem??? almost sounds like it's messing up the files.

---

### Post by SuperMike on 2006-01-20
[QUOTE=Ocxic]will ghost support the ext3 filesystem??? almost sounds like it's messing up the files.[/QUOTE]

You know, that might be it. I had success when we tested this with earlier Fedora builds, but I think those used EXT2 instead of EXT3. That might be it. I'll ask my employee to check on this and let you know.

---

### Post by SuperMike on 2006-01-20
[QUOTE=jstueve]Is the /boot directory in the image?  

*spitballing*[/QUOTE]

Yep. When I expand the image on the Ghost Server, I see /boot and the proper files inside there like I should. We're also using identical hardware -- not a stitch of difference.

---

### Post by SuperMike on 2006-01-20
Okay, let's go *around* Ghost. Let's say I build another Ubuntu 5.10 OS on another kiosk. How do I copy and overwrite everything from one kiosk to the other kiosk, over the Ethernet network? Is there a command in Linux for that?

---

### Post by abrovink on 2006-01-20
[QUOTE=SuperMike]Okay, let's go *around* Ghost. Let's say I build another Ubuntu 5.10 OS on another kiosk. How do I copy and overwrite everything from one kiosk to the other kiosk, over the Ethernet network? Is there a command in Linux for that?[/QUOTE]

[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)
[https://sourceforge.net/projects/g4l](https://sourceforge.net/projects/g4l)

EDIT:Symantec Ghost 7.5 and newer support Ext3 native copies.

---

