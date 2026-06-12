---
title: "Broke my Ubuntu after graphic driver reinstall"
date: 2009-07-28
forum: General Help
---

### Post by tesseract1 on 2009-07-28
I attempted to reinstall some graphic drivers.  I obviously failed and now I can't boot into Ubuntu 9.04.  I tried running recovery graphics fixer, but no help.

I'd imagine there would be a manual fix through Live cd.  I'm not sure what to do.

Basically I need some sort of walkthrough to fix my Ubuntu through the Live cd.  I can't start up.

---

### Post by pastalavista on 2009-07-28
Before trying the live CD, try recovery mode again and open a root terminal with networking. Then enter these commands
```
sudo apt-get update
``` If that works (networking works) then enter ```
sudo aptitude remove xserver-xorg --purge
```and then
```
sudo aptitude install xserver-xorg
```

---

### Post by tesseract1 on 2009-07-29
perfect thank you.

---

### Post by Sepanderi on 2009-07-29
I had a similar problem after updating ATI drivers. Booting ubuntu always crashed with wacky graphical glitches. I managed to fix it by booting to terminal via GRUB's recovery mode. I found out that my xorg.conf was messed up but fortunately there was a bunch of backups of it so I just replaced it with one of 'em and it worked. :)

---

