---
title: "Disable touchpad not working in 12.04"
date: 2012-07-04
forum: General Help
---

### Post by Petro Dawg on 2012-07-04
Has anyone found a real fix for Ubuntu12.04 "Disable touchpad while typing" not working?

I found a work around by installing "touchpad-idicator" which disables the touchpad when I have a mouse plugged in, but the original issue is just masked and reappears if I unplug the mouse.  The program also lets me disable the touchpad through a keyboard short cut, effectively giving it an on and off switch, which is usable, but annoyingly so.

BTW, I have already reported this as a bug.

Thanks in advance for any help with this issue.

If anyone else is in need of the work around you can get touchpad-idicator from the terminal by entering:
[COLOR=red]
sudo add-apt-repository ppa:atareao/atareao[/COLOR][COLOR=red]
sudo apt-get update[/COLOR][COLOR=red]
sudo apt-get install touchpad-indicator[/COLOR]

---

### Post by MarjaE on 2012-07-05
Which touchpad do you have? Does your machine read it as a touchpad or as a ps/2 mouse [with hand motions an inch above registering as double-clicks]?

I have an Alps touchpad and had a lot of trouble with it going haywire, but there is a patch, psmouse-alps-dkms for 11.04. I'm not sure if it's still an issue in 12.04, but if so, you might consider using the patch.

I also used Xubuntu for a while, but they had no touchpad support whatsoever. I couldn't turn the touchpad off and had to reinstall an older version of Ubuntu.

---

### Post by bvlenci on 2012-11-02
I have tried to install this indicator, without success. When I get to the install command, it says "Packet touchpad-indicator not found". The command to add the repository proceeded without generating any error messages, as far as I can see. as did the update command. However, I looked at etc/apt/sources.list and don't see any reference to atareao. Shouldn't the repository be listed?

I tracked atareao down to the atareao team on the Launchpad website, and can see that the package exists in the archive.

---

### Post by bzhao on 2012-11-02
I used touchpad-indicator in the past
But now I add a line of "blacklist psmouse" in /etc/modprobe.d/blacklist.conf
I like the simplicity of the method

---

