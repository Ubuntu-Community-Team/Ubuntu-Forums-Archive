---
title: "GDM sound"
date: 2011-10-09
forum: General Help
---

### Post by quequotion on 2011-10-09
The drum sound in GDM (*not the login sound*) doesn't seem to care what volume you've set for system alerts.

There are a lot of (unresolved) threads about it since many people want to change the volume or turn it off.

The drum sound is played by the .desktop file (launch script): **/usr/share/gdm/autostart/LoginWindow/libcanberra-ready-sound.desktop**

Changed the "Exec" line to add a volume level (be sure to *subtract* decibels). I like **-V -25.0**.```
[Desktop Entry]
Type=Application
Name=GNOME System Ready Sound
Comment=Plays a sound whenever your system is ready for login
Exec=/usr/bin/canberra-gtk-play -V -25.0 --id="system-ready" --description="GNOME System Ready"
OnlyShowIn=GNOME;
AutostartCondition=GNOME /desktop/gnome/sound/event_sounds
X-GNOME-Autostart-Phase=Application
X-GNOME-Provides=login-sound
```

---

