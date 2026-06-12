---
title: "how do you shutdown"
date: 2012-06-15
forum: General Help
---

### Post by js6seaj on 2012-06-15
How do you shutdown? There used to be an item in the top right corner of the screen to do it, but I upgraded and now there isn't one and I can't seem to find a way (other than the power button) to shutdown. :confused:

---

### Post by yiannis66 on 2012-06-15
open the terminal and put
```
sudo poweroff
```

---

### Post by Drenriza on 2012-06-15
> **js6seaj said:**
> How do you shutdown? There used to be an item in the top right corner of the screen to do it, but I upgraded and now there isn't one and I can't seem to find a way (other than the power button) to shutdown. :confused:

I always have a terminal open so i do shutdown -h 0

the 0 is in minutes how long their should go before the command is executed.

---

### Post by lrcaballero on 2012-06-15
> **js6seaj said:**
> How do you shutdown? There used to be an item in the top right corner of the screen to do it, but I upgraded and now there isn't one and I can't seem to find a way (other than the power button) to shutdown. :confused:
  On the right top corner of your desktop next to the time you should see an icon that looks like the KDE icon, click on that and scroll down all the way and you should see the Shutdown option! This is if you are running Ubuntu 12.4 of course.

Cheers,

lrcaballero

---

### Post by nampat on 2012-06-15
shutdown -h now   also works :)

---

### Post by bogan on 2012-06-15
> **js6seaj said:**
> How do you shutdown? There used to be an item in the top right corner of the screen to do it, but I upgraded and now there isn't one and I can't seem to find a way (other than the power button) to shutdown. :confused:Put the Mouse Cursor on the last item in the drop-down Menu and press 'Alt', the 'Shut-Down' option will then show!!

Chao!,** bogan**.

---

### Post by iqtedar on 2012-06-15
They shouldn't have removed it. As Bogan said, press 'Alt' while accessing the user menu and the 'Suspend' option will change to 'Power Off...' For a permanent solution though, go to [https://extensions.gnome.org](https://extensions.gnome.org) and install the gnome extension 'Alternative Status Menu' or 'Quit button' (if you are using Gnome as your desktop environment of course). From the terminal (Alt+Ctrl+T), you can issue the command 'sudo shutdown now'.

---

