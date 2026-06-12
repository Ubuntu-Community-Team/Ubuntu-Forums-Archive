---
title: "no sound in kubuntu with pulseaudio"
date: 2009-11-18
forum: General Help
---

### Post by iliemail on 2009-11-18
some help, please: after i install Kubuntu, i also install another packages in order to have Gnome desktop enviromment too..


Gnome needs PulseAudio for sound so, when i install gnome-core, it also install PulseAudio, as dependency


But, when PulseAudio is installed, i have no sound in Kde... the most obvious solution would be to uninstall PulseAudio and everythingreturn to normal, except the fact that, when i remove PulseAudio, it also removes this applet (in Gnome) from the panel which change the volume


My question: what do i have to do to have this applet back?




(I use Kubuntu 9.10, x64 edition)

---

### Post by Yellow Pasque on 2009-11-18
Get rid of PulseAudio. When in Rome, err, GNOME, use alsamixergui package or some other mixer that isn't dependent on Pulse. You can even use xfce4-mixer if you don't mind some xfce packages being installed.

EDIT: THere might also be a setting in KDE system settings to use or "prefer" ALSA if you want to keep Pulse for GNOME.

---

### Post by iliemail on 2009-11-18
thank you.. i installed some packages, including alsa, and now the applet is back and i have sound in kde and gnome too... thank u again

pulse audio is not installed anymore

---

