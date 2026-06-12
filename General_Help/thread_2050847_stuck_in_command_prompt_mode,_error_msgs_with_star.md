---
title: "stuck in command prompt mode, error msgs with startx"
date: 2012-08-31
forum: General Help
---

### Post by Paco62 on 2012-08-31
I was trying to resolve issues with nvidia card, and the last thing I did was to uninstall and reinstall x server.  (I think I used purge instead of remove).  Now I am stuck in command prompt mode and when I use the command startx I get error messages and then the command prompt again.  Here is a summary of the error messages:

(EE) Failed to load module "nouveau" (module does not exist, 0)
(EE) Failed to load module "vesa" (module does not exist, 0)
(EE) Failed to load module "fbdev" (module does not exist, 0)
(EE) No devices detected

Fatal Server Error:
no screens found

ddxSigGiveUp: closing log
giving up
xinit: No such file or directory (errno 2) unable to connect to x server
xinit: No such process (errno 3) Server error

Can anyone help me get the graphical mode back?   TIA

---

### Post by Bigtime_Scrub on 2012-08-31
I think you uninstalled your graphics card driver. You will need to reinstall it and then try again.

---

### Post by angry_johnnie on 2012-09-01
looks like xserver was removed.


try

```
sudo apt-get install xserver-xorg-video-nouveau
```

---

### Post by Paco62 on 2012-09-02
I solved this by installing xserver-xorg-video-nouveau and xserver-xorg-video-vesa and xserver-xorg-video-fbdev        Thanks for your help

---

