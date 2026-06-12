---
title: "Monitor out of range"
date: 2012-09-06
forum: General Help
---

### Post by JSeymour on 2012-09-06
> **Wild Man said:**
> Hi, here is the answer.
```
gksudo gedit /etc/default/grub
```and change this line:

#GRUB_GFXMODE=640x480

to this:

GRUB_GFXMODE=640x480

Then save and exit the document.
```
sudo update-grub
```On the display setting you can change them to 800x600 while you are then and it will make the screen look a lot better. But do not change them higher you might get a resolution not supported and not be able to boot.
Stupid question, perhaps, but how exactly is one supposed to accomplish that when one can't even get a usable login?

Jim

---

### Post by oldos2er on 2012-09-07
Post moved to its own thread.

---

