---
title: "Pulseaudio"
date: 2011-09-27
forum: General Help
---

### Post by J V on 2011-09-27
Installed a cli version of ubuntu, got everything working under openbox.

Pulseaudio doesn't work when I use my custom ~/.xinitrc file, what should I put there?

Fixed. Apparently ubuntu uses some ****** "consolekit" program which when not started properly screws with the sound.

replace```
exec openbox-session
```
with```
exec ck-launch-session dbus-launch --exit-with-session openbox-session
```

---

### Post by aeiah on 2011-09-27
probably best putting it in ~/.config/openbox/autostart.sh

the pulseaudio daemon is run with the -D flag, so
```

pulseaudio -D
```

[http://linux.die.net/man/1/pulseaudio](http://linux.die.net/man/1/pulseaudio)

---

### Post by J V on 2011-09-27
Thanks, tried that, it didn't work. Any other ideas?

---

### Post by J V on 2011-09-28
Bump, third last thing before completed system, need proper pulse startup (where is it xinitrc for pulseaudio?)

---

### Post by J V on 2011-09-30
BUMP unless I can get pulse working through xinitrc my entire install is a waste of time doesn't SOMEONE know how to start pulseaudio properly??

With "pulseaudio --start" in xinitrc:
```
$ ps aux | grep pulse
j         7210  0.2  0.1 191016  3488 ?        S<sl 11:43   0:00 pulseaudio --start
j         7212  0.0  0.1  96652  3548 ?        S    11:43   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
j         7431  0.0  0.0   7628   932 pts/0    S+   11:44   0:00 grep pulse
```Without xinitrc:```
$ ps aux | grep pulse
j         9299  0.0  0.0   7624   916 pts/0    S+   11:47   0:00 grep pulse
$ vlc videofile
$ ps aux | grep pulse
j         9444  2.5  0.3 278660  7044 ?        S<sl 11:47   0:00 /usr/bin/pulseaudio --start --log-target=syslog
j         9448  0.1  0.1  96652  3544 ?        S    11:47   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
j         9452  0.0  0.0   7624   920 pts/0    S+   11:47   0:00 grep pulse
```Why the hell does sound only work in the second one??

If I leave pulse out of the xinitrc it starts up after something like vlc just fine but it still doesn't play any sound.

---

