---
title: "Need help and fast"
date: 2010-04-27
forum: General Help
---

### Post by markuslee on 2010-04-27
I was doing a complete os install of ubuntu 9.10, at about 45% installation stopped. now my laptop does not have an os and grub will not allow me to aces my bios in order to boot from cd. what should i do?

---

### Post by mcoleman44 on 2010-04-27
Grub comes after bios so this has nothing to do with grub. Or it shouldnt anyway. What happens when you turn the computer on?

---

### Post by limey_rick on 2010-04-27
GRUB has nothing to do with the BIOS and stopping you booting from a CD. Its installed on a MBR of a disk or USB drive so if you can't boot from a CD, its most likely because your computer does not have this set in the BIOS. I think you're saying this, so you want to know how to get into the BIOS? When you start a PC, normally you have to press a key to get into the BIOS. On most PCs, this tend to be the DEL key - have you tried pressing this repeatedly as soon as you boot? Do you get a BIOS boot screen that says press F11 or pres DEL to enter setup or something similar?

---

### Post by markuslee on 2010-04-27
it brings up grub and says error filesystem. i still can't aces bios

---

### Post by markuslee on 2010-04-27
i tried delete, but grub doesn't let you do anything, it doesn't recognize any commands

---

### Post by limey_rick on 2010-04-27
So does this mean that you don't see a start up screen? There is no splash image when you first turn the computer on, before it actually boots?

---

### Post by markuslee on 2010-04-27
no

---

### Post by limey_rick on 2010-04-27
So all I can think of is that your BIOS is set to start without splash screen and possibly a fast boot, so it skips some checks you might normally see to indicate that your PC is starting. 

Is this a laptop or a desktop? If you go online to the support page for the PC (or motherboard if its custom built), can you find a way to reset the CMOS? 

On a desktop you can usually do this with a jumper cable or removing the CMOS battery - on a laptop it may be more tricky. If you do this, I think would reset your BIOS and should bring up a screen next time so you can go into the BIOS menu.

---

### Post by klemes on 2010-04-27
Look forget grub.Grub is installed right at the end of the installation process .You may not even have Grub installed!!!
It may be some hardware issue with your laptop since obviously it does not get even to the POST screen.And that would explain even why it got stuck during the installation.Quiet a coincidence I agree but what else it could be?I recommend unplugging the laptop from the AC current and taking off the battery.Leave it like this for at last 10 minutes and retry to see if this time it will reach POST.If not some laptops have a hardware reset button try to find it if there is one and use it.There's not much else you can do yourself I am afraid.

---

### Post by Shazaam on 2010-04-27
Keyboard keys to try when the laptop/pc FIRST starts (after you press the power button/open the lid) to access the bios...
Delete
F11
F12

---

### Post by QIII on 2010-04-27
Manufacturer, model, specs?

We might be able to find the BIOS access method.

Have you checked to see if the memory modules have jarred loose?

---

