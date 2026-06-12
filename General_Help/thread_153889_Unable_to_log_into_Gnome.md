---
title: "Unable to log into Gnome"
date: 2006-04-01
forum: General Help
---

### Post by JoeyCorless on 2006-04-01
I had everything up and running fine earlier, except that it used to take a long time when booting when it reached the "Configuring Network Interfaces" step.  This was before I had configured my wireless router properly and set everything up.  Now that I got all that working, though, I can't even log in to gnome.  It boots up fine and no longer takes a long time at that step, but now when I enter my username and password to log in the screen goes blank (the brown background, anyway) and it just hangs there.  I can still move the cursor, but nothing happens.  I can do ctrl+alt+backspace and that takes me back to the login screen, but if I try to login again the same thing happens.  It also occurs if I try to log in to a Gnome-Failsafe session.  The only thing that works is logging into a Terminal-Failsafe session.  Has anyone encountered something similar, or is there some way to fix it?  Thanks for any help.

Info:
The computer is a Compaq Presario V2000z.  Turion ML-37 processor.  ATI Radeon XPress 200M. Broadcom 802.11b/g WLAN.
I'm running version 5.10 of Ubuntu, but I also have a Windows partition (using Grub for booting).

---

### Post by dcstar on 2006-04-02
[QUOTE=JoeyCorless]I had everything up and running fine earlier, except that it used to take a long time when booting when it reached the "Configuring Network Interfaces" step.  This was before I had configured my wireless router properly and set everything up.  Now that I got all that working, though, I can't even log in to gnome.  It boots up fine and no longer takes a long time at that step, but now when I enter my username and password to log in the screen goes blank (the brown background, anyway) and it just hangs there.  I can still move the cursor, but nothing happens.  I can do ctrl+alt+backspace and that takes me back to the login screen, but if I try to login again the same thing happens.  It also occurs if I try to log in to a Gnome-Failsafe session.  The only thing that works is logging into a Terminal-Failsafe session.  Has anyone encountered something similar, or is there some way to fix it?  Thanks for any help.

Info:
The computer is a Compaq Presario V2000z.  Turion ML-37 processor.  ATI Radeon XPress 200M. Broadcom 802.11b/g WLAN.
I'm running version 5.10 of Ubuntu, but I also have a Windows partition (using Grub for booting).[/QUOTE]
I believe you are still running the old version of your video driver and you have to manually update to the Breezy version.

CTRL-ALT-F1 and:
```
sudo dpkg-reconfigure xserver-xorg
```
Select the VESA driver and that should get you going in a basic manner.

Do a forum search for detailed instructions on upgrading your video driver.

---

### Post by JoeyCorless on 2006-04-02
Thanks for the suggestion, but I'd actually already installed the new driver, so that wasn't the problem (that was an earlier problem that I had and fixed).  I'm still not sure what the problem is now but I've found a way around it.  I noticed that if I skip the "Configuring Network Interfaces" setup on startup (using ctrl+c) everything would work fine except that I'd have to manually enable wlan0.   So I just commented out "auto wlan0" from my /etc/network/interfaces file and now it works fine.  I have no idea why that was causing a problem, maybe something with my wireless settings, but this solution works for now.

---

