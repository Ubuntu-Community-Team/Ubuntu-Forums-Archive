---
title: "ubuntu (normal generic kernel) imaging qustion"
date: 2009-07-23
forum: General Help
---

### Post by Meow27 on 2009-07-23
if i make an image of ubuntu on a certain generation dell PC and then image it, and burn it on another computer with a different but similar model, will i be suffering any problems?


i know this can happen with windows, but since ubuntu has rather generic settings, i was thinking i might not have to worry about backing up a desktop for specific models

---

### Post by Bucky Ball on 2009-07-23
Yes, for one the resolution will probably be wrong. It is exactly the same as Windows in as much as it finds your hardware when you install it and configures accordingly. If you install same on another machine and expected hardware or chipsets are absent, you could be in some trouble.

---

### Post by kdetech on 2009-07-23
I have installed normal cd of kubuntu in pendrive and its completely portable. No resolution problems or anything. In fact I once transfered A hard drive from pc to pc. Windows crashed (blue screen) but ubuntu worked fine.

IF YOU HAVE NVIDIA DRIVER INSTALLED YOU WILL HAVE TO RECONFIGURE X MANUALLY if tranfering to a pc with intel or ATI card.

---

### Post by t4thfavor on 2009-07-23
I have moved hard disks between totally dissimilar machines, and had no issues. If you are moving from intel/amd/NvidiaGraphics to any/NvidiaGraphics you shouldn't have problems.


if you are moving between something with nvidia graphics to something with other graphics, you will have to reconfigure the xserver.


I moved an hdd from a dual pIII 600 to an athalon 3000+ and had no issues since the samg gfx card was used on both.

---

