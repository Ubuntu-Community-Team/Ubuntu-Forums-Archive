---
title: "Cannot access LXDE, KDE from login"
date: 2012-01-03
forum: General Help
---

### Post by oldrocker99 on 2012-01-03
I installed kde-full last night and selected (apparently) the wrong display manager. My login screen is for Lubuntu (I have LXDE installed), and I cannot log into LXDE or KDE; the login screen asks for my username(?) and password, then blanks for a second and returns to asking my username](*,). I CAN log on and get into LXDE, MATE, Openbox and a couple of others, but I WANT to run XFCE or KDE from the login screen directly. I'm running XFCE now, which I started from LXDE using the --replace option, but this is not a solution.

A Google search gave a solution, but it involved this command:
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow

The problem being that gnome-appearance-properties.desktop is not present in /user/share/applications...

Any ideas? I'd actually like to get back to the Linux Mint login screen, but I'm having...problems.:cry:


[SOLVED]:D
OK, reading about someone else's more severe problem inspired me to sudo reconfigure-gdm, which allowed me to pick a different display manager, and now I'm in XFCE happily.

---

