---
title: "Want to change Ubuntu from using motherboard video"
date: 2006-05-06
forum: General Help
---

### Post by Rundi on 2006-05-06
Sorry if my terminology isn't quite right but here is my story of woe:

I have Intel integrated video. I also have an ATI Rage Pro video card that I am trying to get Ubuntu to use. The ATI card is recongized in the device manager, but I seem unable to get X to use it. Whenever I do an auto-detect X keeps plugging in the Intel integrated. I then manually put in the info for the ATI Rage Pro (PCI bus location, etc) and it doesn't work. When I boot to the GUI I get a blank screen. I only get visual if I switch to console (which isn't using X)

I think (and this is where my ignorance really comes in to play) that X is trying to find my monitor from the intel integrated port even though I specified the PCI bus location for the ATI card. In the X error log I get says something like "Could not find Screen 0" which leads me to believe it is looking for "Screen 0" at the integrated graphics location.

Any help would be much appreciated. Thanks.

---

### Post by chicken101 on 2006-05-07
[QUOTE=Rundi]Sorry if my terminology isn't quite right but here is my story of woe:

I have Intel integrated video. I also have an ATI Rage Pro video card that I am trying to get Ubuntu to use. The ATI card is recongized in the device manager, but I seem unable to get X to use it. Whenever I do an auto-detect X keeps plugging in the Intel integrated. I then manually put in the info for the ATI Rage Pro (PCI bus location, etc) and it doesn't work. When I boot to the GUI I get a blank screen. I only get visual if I switch to console (which isn't using X)

I think (and this is where my ignorance really comes in to play) that X is trying to find my monitor from the intel integrated port even though I specified the PCI bus location for the ATI card. In the X error log I get says something like "Could not find Screen 0" which leads me to believe it is looking for "Screen 0" at the integrated graphics location.

Any help would be much appreciated. Thanks.[/QUOTE]


This is an easy one.  Reboot your computer and get into the bios (press delete or f1 on boot-up).  You should be able to disable the onboard video chip from there.  Cheers!

---

