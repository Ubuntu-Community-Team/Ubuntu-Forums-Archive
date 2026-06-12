---
title: "Cellwriter does not work anymore. It doesn't pop up"
date: 2009-09-29
forum: General Help
---

### Post by samathyr on 2009-09-29
Hi, I am using a Tablet PC (Asus R1E under Ubuntu 8.10) and I got a problem with my Cellwriter software (which I used a lot)

It doesn't pop up when I click on the tray icon, nothing I can do from the GUI can make it appear, even settings don't appear at the screen. I think the problem is that the program is opening in an unused area of the screen, out of range (remember the tablet pc can freely rotate the screen and expand/contract the desktop)

How can I make it appear?
Someway to reset the x-y coordinates where it pops up at 1,1 or something similar?

I have tried Complete Removal from Synaptic and Install Again and Complete Removal from Synaptic and Install from .deb file found at the developer's website.

Thank you for your help

---

### Post by samathyr on 2009-10-02
Up... I need to solve this problem

Think of this as : how can I modify the area where something is supposed to pup up?

---

### Post by Favux on 2009-10-02
Hi samathyr,

It could be hiding behind a panel.

You may have rotated it off screen.  Try right clicking on it and see if you can get into setup.  You may need to alternate between show and hide.  Then in "Window docking" tell it Top.  Then go back to Window docking and disable again.  See if it's now on screen.

---

### Post by samathyr on 2009-10-02
No... it doesn't appear... I cannot even put it "on Top"

How do I delete it for good? So when I install it everything will be like the first time?

Thanks

---

### Post by Favux on 2009-10-02
Hi samathyr,

First try alt+F2 and enter:  cellwriter --show-window

If that doesn't work quit CellWriter and restart it with (in alt+F2):  cellwriter --show-window --window-y=600 &

You can completely uninstall including the configuration files through Synaptic Package Manager.  Search for it, right click and tell it complete uninstall.

---

### Post by samathyr on 2009-10-03
thank you favux!!

now it works like charm :D

thanks!!

---

### Post by Favux on 2009-10-03
Hi samathyr,

Great!  You're welcome.

If it was the second line, the one with the y coordinate, that worked you could put it into a launcher.

---

