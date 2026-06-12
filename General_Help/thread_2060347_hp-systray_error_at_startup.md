---
title: "hp-systray error at startup"
date: 2012-09-19
forum: General Help
---

### Post by kleinempfaenger on 2012-09-19
Hi,
I use Ubuntu 12.04 with Cairo-Dock.
Hplip shows an error message at startup: "No System-Tray detected".
Searched a bit and saw that the problem existed some years ago on Jaunty. Hp-systray sometimes starts before starting systray, so in hplip-systray.desktop file in /etc/xdg/autostart a parameter was changed to delay startup.

Quote:
sh -c "sleep 15; exec hp-systray"
I changed 15 to 45, and ever since no error message at startup."


Opened that file with gedit, but in Precise that line doesn't exist any more:

[Desktop Entry]
Version=0.6
Type=Application
Name=HP System Tray Service
GenericName=Printer Status Applet
Comment=HP System Tray Service
Exec=hp-systray
Icon=/usr/share/hplip/data/images/128x128/hp_logo.png
Terminal=false
Categories=Application;Utility;
X-KDE-StartupNotify=false
StartupNotify=false

Tried to insert sh-line from above in line "Exec=hp-systray", but hp-systray wouldn't start any more at startup. How could I delay startup of hp-systray or solve the problem any other way?


Thanks and greetings,
kl

---

### Post by GeForce 9500GT on 2012-09-20
I found the same, just for Jaunty. But here they [provide a bugfux]("https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/335662") but for jaunty...
Here also [a solution]("https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/153906"), but that's for Gnome panels...
 
Which version of HPLIP do you have installed? Normnally the version which has been shipped with Ubuntu 12.04 is older than the version available on the website of HPLIP. Maybe you can try updating your HPLIP driver.

---

### Post by kleinempfaenger on 2012-09-20
Oh thanks, this one is solved. Upgrade to hplip 3.12.9 from 3.12.2 did it. Everything is working fine now, hp-systray at startup without problems.

Greetings, kl

---

### Post by kleinempfaenger on 2012-09-30
After some days of correct working, problem again happening.
New version is still installed, system actualized.
How could I delay hplip-lauch at startup?

Thanks, kl

---

