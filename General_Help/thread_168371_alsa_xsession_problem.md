---
title: "alsa xsession problem"
date: 2006-04-30
forum: General Help
---

### Post by yamca on 2006-04-30
I have a MSI M635 laptop. I installed Ubuntu 5.1,got the latest updates,installed codecs with Automatix, installed radeon drivers. 
Everything went fine it recognized my sound card but i cant get any sound.
Then i installed alsa again manually. But when i try to login my account it gives an error:
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xsercvers" -h "" -l ":0" "root"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/gnome-session: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory

Sound card: Realtek AC97

---

