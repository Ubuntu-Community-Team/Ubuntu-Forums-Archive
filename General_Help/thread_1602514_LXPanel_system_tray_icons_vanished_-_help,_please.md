---
title: "LXPanel system tray icons vanished - help, please"
date: 2010-10-21
forum: General Help
---

### Post by dalinian on 2010-10-21
I'm having some trouble with a SmartDevices SmartQ V7 Linux tablet. :(
• OS: SmartDevices 'Linux v5.5', which is I understand Ubuntu 9.10, downloaded and re-flashed on Thursday 30 September 2010.
• bootloader: the latest, I believe: boot screen background is black with blue/red corners.

After a minor edit to /home/user/.config/openbox/lxde-rc.xml (to get leafpad to always launch maximised), four icons in my lxpanel system tray have vanished. The WiFi and clock are still there, but the keyboad, volume, brightness and battery icons are missing. #-o

On booting the following two error messages appear, one after the other:
• get the keyboard image failed!
• Load pmctl's image failed!

I've composited four screengrabs to illustrate how it used to look before, the current boot sequence error messages, how it looks now, and the contents of /usr/lib/lxpanel/plugins:
[ATTACH]173053[/ATTACH]

Googling these error messages in double quotes yields zero results. I've tried restoring the original lxde-rc.xml and rebooting, but the problem persists. No doubt re-flashing the firmware would fix this, but that would also entail countless OS tweaks and software reinstallations, so I'd prefer to avoid such a sledgehammer-to-crack-a-nut solution if possible. 

I can haz Linux guru hlp plz??? 

Kthxbai :biggrin:

---

