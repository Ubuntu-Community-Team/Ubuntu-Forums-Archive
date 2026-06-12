---
title: "Xorg configuration"
date: 2009-08-17
forum: General Help
---

### Post by Janis Janovskis on 2009-08-17
Hi

I used Sympatic to remove some not needed programs un Ubuntu 9.04,
After rebooting I got tty 1 mode.
I did not give up - wrote start x

I got out message - (EE) failed to load module "vesa" (module does not exist)
                             (EE) no drivers instaled
 I tried reconfigure xrog, but it did not gave me any possibilities to find any vesa drivers at all - there were only keyboard selection options.

What to do has any one some solution, are there any possibilities or shoul I reinstall the system?

Help

Janis

---

### Post by Strongman332 on 2009-08-17
hit the 'e' button at the grub screen then boot safe grafics mode then have it fix x for you (should work). if you have tryed this you can use the comand line option to reinstall any part of the grafics system

---

### Post by Thelasko on 2009-08-17
No need to configure xorg anymore.  Everything is automatically detected upon boot.

My guess is that you removed something critical accidentally.  Try running ```
sudo apt-get install ubuntu-desktop
```
Hopefully that will install whatever components are missing.

good luck

---

### Post by Janis Janovskis on 2009-08-17
> **Thelasko said:**
> No need to configure xorg anymore.  Everything is automatically detected upon boot.

My guess is that you removed something critical accidentally.  Try running ```
sudo apt-get install ubuntu-desktop
```Hopefully that will install whatever components are missing.

good luck

Sorry does not help anything

---

### Post by Thelasko on 2009-08-17
try```
sudo apt-get install xserver-xorg-video-vesa
```
and see if that fixes anything.

---

