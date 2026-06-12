---
title: "Top panel right side buttons missing"
date: 2011-04-18
forum: General Help
---

### Post by ScroobeX on 2011-04-18
Hi there, thanks for reading this. I was wondering if one of you can help me, few days ago after doing several updates the buttons on the right hand side of the top panel have just dissapeared, with several messages about errores in applets and whether I would like to turn them off because they are not there or are missing (if I remember correctly), so after that the "start/shutdown button" and other buttons are missing, while the programs and system menu on the left hand side is unaffected.

Can anyone please tell me if there's a procedure to get it back :P


Cheers

---

### Post by lhowaf on 2011-04-18
You might try re-installing the indicator-applet (maybe indicator-applet-session?).

---

### Post by ScroobeX on 2011-04-18
Well perhaps but I'm not really sure how this is done

---

### Post by lhowaf on 2011-04-18
Open: System | Administration | Synaptic Package Manager and type > indicator in the Search box. Find  indicator-applet-session in the resultant list and click the box. If it was already installed, there will be an option in the pop-up dialog to re-install. If it hadn't been installed, there will be an option to install it.
You could also just open a terminal and type, > sudo apt-get install indicator-applet-session.

---

### Post by ScroobeX on 2011-04-19
Is that indicator for gnome only? I've done the reinstall as well as reinstall of all indicators in synaptic and it does not do the trick. It's not there.

---

### Post by lhowaf on 2011-04-19
Yes. you're right. I believe it is the "plasma-widget-menubar" for Kubuntu.

---

### Post by ScroobeX on 2011-04-22
Yeah well I tried to uninstall-reinstall them too, and didn't do the trick. Pity, it seems there is no solution to this particular problem.

---

