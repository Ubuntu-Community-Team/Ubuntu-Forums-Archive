---
title: "Help needed using PekWM as drop-in replacement for Openbox."
date: 2010-11-07
forum: General Help
---

### Post by casbahdk on 2010-11-07
I am experimenting with PekWM as a drop-in replacement for Openbox on a Peppermint Ice (Lubuntu derivative) system installed on my Eee PC 701. I am trying to get the same look and feel as per Openbox and have largely succeeded by simply copying the parameters in the /etc/xdg/lxsession/Peppermint_ice/autostart file and pasting them into the ~/.pekwm/start file, replacing the "@" signs at the beginning of each line and adding an "&" sign at the end of each line and running chmod +x ~/.pekwm/start.

Unfortunately I am experiencing problems with window and menu freezes (the panel clock works during the freezes) and the "logout" buttons in the lxpanel menu and at the far right of the panel don't function.

My ~/.pekwm/start file looks like this:

nm-applet &
lxpanel --profile Peppermint_Ice &
xscreensaver -no-splash &
gnome-power-manager &
pcmanfm --desktop &
mintinput1 &
xdg-user-dirs-gtk-update &
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 &

What am I doing wrong? I don't see any problem with the syntax in the start file.

---

