---
title: "problem installing ubuntu 12.04"
date: 2012-10-05
forum: General Help
---

### Post by owentm on 2012-10-05
Greetings,

I'm trying to install Ubuntu 12.04 on my old HP pavilion dv6000 laptop over Windows Vista. I've downloaded the 12.04 .iso and flashed it to a 4gig usb stick using [universal usb installer](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) from pendrivelinux.com.

When I boot to the flash drive, the graphics on my computer crap out. I dont have a blank black screen as almost all the google help searches yielded, but rather a series of vertical partitions, where the mouse or text only displays in certain sections. (I'll have a picture up as soon as my phone can finish emailing it to me).

It seems to be a problem with the video card drivers. several forums/topics said stuff about noquiet and nosplash, but I cant seem to find anything of the sorts.

I can press ctrl+alt+F2 and get to terminal, but I cant find a forums detailing how to fix it that way. 


keep in mind, ubuntu is not installed on my machine yet. any help would be appreciated!

thanks
~Tim

---

### Post by owentm on 2012-10-05
this is what i'm talking about...

[img]http://img.photobucket.com/albums/v663/Drowning_Fetus/IMAG0450.jpg[/img]

---

### Post by Bashing-om on 2012-10-05
Tim; Hi ! Welcome to the forum.

It does appear to be a graphics driver issue. There are solutions:
boot the install disk, when bios screen clears, depress any key =>boot options menu
the f6 key selects "nomodeset"
f10 key continues the boot.

Can you now boot into ubuntu ?
system settings(launch left side of screen)->additional drivers / see if an appropriate driver can be loaded.

This  link for full/additional information:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

In the event this does not resolve the situation. post back with updated info.

[INDENT]warm regards <==BDQ

[/INDENT]

---

