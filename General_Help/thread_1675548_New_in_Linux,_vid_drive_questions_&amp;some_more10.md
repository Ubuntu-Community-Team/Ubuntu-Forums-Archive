---
title: "New in Linux, vid drive questions &amp;some more/10.10/"
date: 2011-01-25
forum: General Help
---

### Post by valqkaaa on 2011-01-25
Hello

Yesterday I installed ubuntu 10.4 but when I installed my video drivers from sys/adm/drivers and then restarted the PC I got a black screen. My video card is GeForce 9800 GT. Then I reinstalled ubuntu but I put the 10.10 version. Have you got any ideas why is this happening and how can I install drivers for my video card without getting the freaking black screen. The worst thing is that when I get it I don't know how to fix it because linux doesn't have Safe Mode like Windows.

Other questions if you have time for answering:
-how to turn off the timed hibernate?
-how to turn off the persisting password requiring? (after hibernate, before installing software, etc.)
-do I need drivers for my P5KPL (c2d 2.2) and where to find one for Ubuntu?

That is for now. Thank you in advance. Sorry for the ultra stupid questions but I'm still a newb.

Version of Ubuntu 10.10

---

### Post by valqkaaa on 2011-01-25
Bump....

---

### Post by mikewhatever on 2011-01-25
> **valqkaaa said:**
> Hello

Yesterday I installed ubuntu 10.4 but when I installed my video drivers from sys/adm/drivers and then restarted the PC I got a black screen. My video card is GeForce 9800 GT. Then I reinstalled ubuntu but I put the 10.10 version. Have you got any ideas why is this happening and how can I install drivers for my video card without getting the freaking black screen. The worst thing is that when I get it I don't know how to fix it because linux doesn't have Safe Mode like Windows.

You may need to run the **nvidia-xconfig** command from the recovery mode. I hope you understand that it's not like Windows because it's not Windows.

> 
Other questions if you have time for answering:
-how to turn off the timed hibernate?
-how to turn off the persisting password requiring? (after hibernate, before installing software, etc.)


-System->Preferences->Gnome Power Manager
-The password is required, again, it's not Windows.

---

### Post by sikander3786 on 2011-01-25
Welcome to the forums :-)

Regarding you video issue, press and hold down shift key from Bios screen until you see the Grub menu. Select the 2nd entry there (Recovery Mode) and then, Drop to root shell prompt. Follow these commands for reconfiguring your graphics.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bad
```

Remember, all the commands are case sensitive. Note capital 'X' for X11.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo reboot now
```

Let us know how that goes.

Regarding the hibernate question, screen saver also kicks in after a period of 10 minutes and requires a password to continue your session. You can change the settings under System > Preferences > Screen Saver.

---

### Post by Elfy on 2011-01-28
Duplicate closed.

---

