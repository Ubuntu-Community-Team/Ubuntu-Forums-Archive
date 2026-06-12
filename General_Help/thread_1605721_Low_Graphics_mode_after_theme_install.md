---
title: "Low Graphics mode after theme install?"
date: 2010-10-25
forum: General Help
---

### Post by mishypie on 2010-10-25
Hi,

Running Ubuntu 10.10 on a Dell PC

I recently installed a theme called [Faezna]("http://tiheum.deviantart.com/art/Faenza-Icons-173323228") and now Ubuntu always runs in low graphics mode :(

I have
  -Uninstalled and deleted theme files
  -Changed theme back to default theme
  -Rebooted several times
  -Restored graphics settings in low graphics mode (pre-boot menu thing)
  
The thing that makes it worse is that the theme never even worked in the first place and T never got to see it!

Any help would be appreciated, thanks.

---

### Post by sikander3786 on 2010-10-25
Your graphics card really hates that theme. Angry coz you installed that ;-)
Sorry, couldn't resist :-)

Did you try reconfiguring graphics from Recovery Mode?

---

### Post by mishypie on 2010-10-25
> **sikander3786 said:**
> Your graphics card really hates that theme. Angry coz you installed that ;-)
Sorry, couldn't resist :-)

haha probably, my graphics card is terrible
> 
Did you try reconfiguring graphics from Recovery Mode?

not sure what you mean, but I reconfigured graphics in the menu that comes up when Ubuntu tells you you need to use Low Graphics mode.

---

### Post by sikander3786 on 2010-10-25
Do you see the Grub menu by default? If not hold down the Shift key from the Bios screen to see it. From Grub menu, select recovery mode, most probably the 2nd one on the list and then "Reconfigure Graphics" or something like that.

If it doesn't help, tell us which graphics card are you using. Did you install any proprietary drivers for it?

---

### Post by mishypie on 2010-10-25
Ok I booted into recovery mode, but there was no option to reconfigure graphics, however I did get error messages reading:

(EE) drm failed to open
(EE) failed to initiate GLX (NVIDIA driver not found)

I then assumed I would need to re-install the driver for my graphics card, but could not do this- followed the installation instructions but it just wont do it. 

Any suggestions?

Im using an NVIDIA GeForce FX5200

---

