---
title: "Trying to set up Compiz - cant find xgl"
date: 2009-08-18
forum: General Help
---

### Post by tim8410 on 2009-08-18
So Im trying to set up compiz, but after searching numerous times i cant find any of the xgl packages in synaptic. Same thing goes for trying to install from a terminal--it says the package doesn't exist, and I ran the aptitude update command and everything, still no luck.

---

### Post by tim8410 on 2009-08-18
bump

---

### Post by Cheesemill on 2009-08-18
What exactly are you trying to do?
Compiz is already included in a standard Jaunty install.

---

### Post by tim8410 on 2009-08-19
when i try to run compiz --replace errors show up saying i dont have xgl

---

### Post by jocko on 2009-08-19
> **tim8410 said:**
> when i try to run compiz --replace errors show up saying i dont have xgl
That's not an error. It's just information about which methods compiz tries to use. xgl is not needed anymore.
If you want help with compiz, you need to give us some more information about your computer:
1. What graphics card do you have?
2. Which driver does it use?
3. What does compiz say when you try to run it in a terminal? Paste the whole output.

---

### Post by mcduck on 2009-08-19
> **tim8410 said:**
> So Im trying to set up compiz, but after searching numerous times i cant find any of the xgl packages in synaptic. Same thing goes for trying to install from a terminal--it says the package doesn't exist, and I ran the aptitude update command and everything, still no luck.

Are you following some guide to do this? In that case your guide is seriously outdated..

Compiz has been included by default in the couple of latest Ubuntu releases, and XGL isn't really usually used any more since current graphics card drivers already support better ways to handle this kind of stuff.

To get Compiz working just go to System/Preferences/Appearance, and on the Visual Effects-tab set them to "Normal" or "Extra". IF you want, then install CompizConfig Settings Manager to adjust the settings as you like.

If that doesn't work, make sure you have drivers for your graphics card correctly installed and working.

---

### Post by 3rdalbum on 2009-08-19
You need to go to System > Administration > Hardware Drivers and click "Activate" on the Nvidia driver that will be offered (I'm assuming you're still using your machine with the GeForce 5200).

XGL is not needed anymore and Compiz comes preinstalled. Any guide you are using that involves "installing Compiz" is waay too old.

---

### Post by Barafu Albino Cheetah on 2009-08-19
In case you have no hardware drivers to activate, compiz still should work, but with a heavy CPU load.

---

### Post by tim8410 on 2009-08-19
im on a a laptop that has an intel graphics card in it. thanks for the help. i was searching the forums for help and apparently was finding outdated threads. i though at first compiz wasnt working but i see now that it is and the effects are working. thanks for your help.

---

### Post by ithinkitschad on 2009-08-19
If your still having any problems its really easy to revert the driver to the one that works. [Heres the link]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")

---

