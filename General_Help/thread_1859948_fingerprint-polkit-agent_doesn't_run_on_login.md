---
title: "fingerprint-polkit-agent doesn't run on login"
date: 2011-10-14
forum: General Help
---

### Post by cogcog on 2011-10-14
I just upgraded from 11.04 to 11.10, and I noticed that applications can no longer request su privileges graphically. This turns out to be because the policykit agent, fingerprint-polkit-agent, isn't running. If I execute

/usr/lib/fingerprint-gui/fingerprint-polkit-agent -d

in a terminal, then everything works as normal thereafter. But I can't work out why this isn't being executed on login. There is a file /etc/xdg/autostart/fingerprint-polkit-agent.desktop, which has the following entry:

[Desktop Entry]
Name=PolicyKit Authentication Agent with Fingerprint Authentication
Comment=PolicyKit Authentication Agent with Fingerprint Authentication
Exec=/usr/lib/fingerprint-gui/fingerprint-polkit-agent -d
Terminal=false
Type=Application
Categories=
NoDisplay=true
OnlyShowIn=GNOME;XFCE;KDE;
X-GNOME-AutoRestart=true
X-Ubuntu-Gettext-Domain=polkit-gnome-1

I also tried copying this file to ~/.config/autostart, but it still doesn't run on login.

For some reason, this problem only happens in the unity shell: if I log in with the gnome-shell interface, it works. I tried adding "Unity;" after the OnlyShowIn line, but this makes no difference.

---

### Post by malinkb on 2011-10-27
I experience the same issue, but I haven't found a solution for it.
I tried to start the polkit-agent manually, and then it works, but after a reboot or new login, it doesn't.
I tried to make a new user with admin privileges and logged in, then it worked.

I have this same issue even after a clean install, but mye /home folder is the same, so I guess that's the place to investigate.

Edit:

What happens, if you do this?

mv ~/.config/autostart ~/.config/autostart.backup && mkdir ~/.config/autostart

and log out and in again

---

### Post by cogcog on 2011-11-09
Hi! I didn't see this response before for some reason. I tried your suggestion, and it works perfectly. Thanks!

I guess there was a conflict with something in the user-specific startup items that got carried over from my previous installation, but since there was nothing in there I care about I just left the new directory empty.

---

