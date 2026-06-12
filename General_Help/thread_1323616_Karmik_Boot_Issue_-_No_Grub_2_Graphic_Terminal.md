---
title: "Karmik Boot Issue - No Grub 2 Graphic Terminal"
date: 2009-11-11
forum: General Help
---

### Post by ahnise on 2009-11-11
Hi,

I recently upgraded from Jaunty to Karmik on an Acer 6291 Laptop. I am having the following issues:

1) GRUB2 is not displaying the graphical menu - it is defaulting to the text screen. 

2) Long Boot Time (around 65 seconds from Grub selection to functional desktop

During the boot process, I see the following:
*GRUB Menu Loads in text mode (version 1.97)
*Graphical boot display (with static ubuntu logo)
*Screen goes black with login prompt
*A few seconds later boot process continues (with graphical animated horizontal bar
*graphical login appears
*Gnome loads (in about 40 seconds)

This installation was a fresh install of Karmik where I reformatted the root partition (for storing the OS), and preserved my home directory partition.

---

### Post by bashphoenux on 2009-11-11
yes mate unfortunately many of us are facing that the boot time is more in Karmic !! not to be surprised but the above mentioned steps occurs for everyone !! 
regarding splash screen check[ this]("http://www.howtoforge.com/how-to-add-a-splash-image-to-grub-2-on-ubuntu-9.04")

---

### Post by ahnise on 2009-11-11
Thanks so much for your fast reply - really appreciate it.  I took a look at your link, the issue I am having is not the inclusion of a bitmap background, but that grub is not going into the graphical terminal mode (where you get a blue background and mouse functionality) It seems to be defaulting to the text terminal mode. My understanding was that if grub2 installs correctly, you will see a pretty blue screen and have mouse functionality. My screen is displaying black and white text (with no mouse) like the old grub.  How did your Grub screen look when you first installed Karmik ?

---

