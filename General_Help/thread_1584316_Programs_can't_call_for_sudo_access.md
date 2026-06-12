---
title: "Programs can't call for sudo access"
date: 2010-09-29
forum: General Help
---

### Post by kyfho23 on 2010-09-29
Hi,
   Let me see if I can put this coherently: Programs that require super user authentication AFTER they have been launched (for instance,in the time settings applet, you have to sudo authenticate to update the clock, but not just to open the applet. Another instance is Ubuntu-Tweak, which requires admin rights for some of it's functions.)

A couple of clues:
   This has persisted over a re-install.
   I have a separate /home partition.
   I can call the programs from the command-line using "gksu whatever".
   I don't get a flash or any signal. Usually, nothing happens. Ailurus gave me a message "Operation is canceled because you refused authentication. Authentication is provided by system PolicyKit service. Ailurus does not know your password at all."
   PolicyKit is NOT among my startup programs. Investigating further...

UPDATE: SOLVED Ubuntu-Tweak showed PolicyKit as starting; System/Preferences/Startup Applications DID NOT. So I copied the information from Ubuntu-Tweak: (First, check off "Show All Runnable Programs" and "Show comments") Auto-Start Programs/PolicyKit Authentication Agent, highlight it, then click "Edit" on the upper right. Then open System/Preferences/Startup Applications and click Add, again in the upper right. Just copy the information over from the Ubuntu-Tweak window to the Startup window you have open. Reboot. Enjoy.


Any other information provided on request. I'm using Ubuntu 10.04.1, all updates applied.

---

### Post by sisco311 on 2010-09-29
Most modern GUI apps use [policykit]("http://hal.freedesktop.org/docs/polkit/") instead of sudo/gksu. The authentication agent must run in your user's session in order to provide the authentication dialog when needed. 

Somehow you managed to disable the authentication agent from the Startup Applications and because you have a separate home partition the settings persisted over a re-install.

---

### Post by kyfho23 on 2010-09-29
Exactly. I'm just glad I found the command to paste in the startup list so easily.

---

### Post by sisco311 on 2010-09-29
I'm glad too! [noparse]:)[/noparse]

If you or someone else is wondering, the system wide Autostart Directory is /etc/xdg/autostart/ and the the one in the user's home directory is ~/.config/autostart/.

But not all of the apps are displayed in gnome-session-properties (System -> Preferences -> Startup Applications). 

i.e., /etc/xdg/autostart/polkit-gnome-authentication-agent-1.desktop:
```
[Desktop Entry]
Name=PolicyKit Authentication Agent
Comment=PolicyKit Authentication Agent
Exec=/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
Terminal=false
Type=Application
Categories=
**NoDisplay=true**
OnlyShowIn=GNOME;XFCE;
X-GNOME-AutoRestart=true
X-Ubuntu-Gettext-Domain=polkit-gnome-1
```

---

