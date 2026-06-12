---
title: "LowGraphic Mode"
date: 2010-02-27
forum: General Help
---

### Post by Kenta92 on 2010-02-27
I had problems with the resolution and my screen couldn't work with that one, so i changed it manually and not it works.
The problem is that at the beginning a window says Ubuntu is running in Low Graphic mode, and i have everytime to choose "work in LowGraphic mode for this time".
I don't really have problems because of it as i'm running Xubuntu most of the times and so i don't need a good graphic, but it's quite boring to do the same operation eveytime i choose to start Ubuntu (both Gnome and Xfce).

I got this problem:
fatal server error
server is already active for display 0
   if this server is no longer running, remove /tmp/.X0-lock and start again

(WW)xf86CloseConsole: KDSETMODE failed, bad file descriptor
(WW)xf86CloseConsole: VT_GETMODE failed, bad file descriptor
(WW)xf86CloseConsole: VT_GETSTATE failed, bad file descriptor

ddxSigGiveUp: Closing log




Any advice?

---

### Post by Kenta92 on 2010-02-28
bump

---

### Post by Kenta92 on 2010-03-01
no one?

---

### Post by nightwolf2k5 on 2010-03-01
You could try modifying your xorg.conf file that is present in /etc/X11.

Modify it as mentioned below:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Note: If you are running Karmic Koala, there will not be any xorg.conf file and when you do a "sudo nano xorg.conf", the file will be created for you. Add the section mentioned above. Save and restart.

Hope it works.

---

### Post by Kenta92 on 2010-03-01
I did that (I have Karmic) but it didn't work..

---

### Post by Kenta92 on 2010-03-03
bump

---

### Post by nightwolf2k5 on 2010-03-10
i think when you get the option "work in LowGraphic mode for this time", there is also another option to reconfigure.
Have you tried that option?

---

### Post by Kenta92 on 2010-03-11
sure, but nothing changed

---

### Post by flippo on 2010-03-11
You posted that your had an error about multiple xorg servers running.  Does this pop up every time you boot your system?  If so you should delete the file they tell you to.  

You can also try deleting (or renaming) your xorg.conf.  The newest version of the Xorg server auto-detects your hardware, so unless your doing something out of the ordinary you actually don't need a xorg.conf.

Also:
What graphics card/drivers are you using?
Can you attach your /var/log/Xorg.0.log?

---

