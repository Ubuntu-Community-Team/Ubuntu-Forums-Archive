---
title: "dbus and gnome"
date: 2006-06-18
forum: General Help
---

### Post by paulyche on 2006-06-18
I can get into GDM, but gnome sessions crash with this error:

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /v ar/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "paul"
/etc/gdm/Xsession: Beginning session setup...
Failed to start message bus: Failed to read directory "/usr/local/share/dbus-1/services": No such file or directory
EOF in dbus-launch reading address from bus daemon

```

I can load a failsafe gnome session.
/usr/local/share/dbus-1/services doesn't exist,

but /usr/share/dbus-1/services does.

I don't know much about startup scripts but it seems they are pointing to the wrong thing, but I don't know why?

I'm a bit lost now.

---

### Post by paulyche on 2006-06-20
bump

---

### Post by saceirdoth on 2006-06-22
up, same problem

---

### Post by az on 2006-06-22
Is the ubuntu-desktop package installed?  Boot into recovery mode (from grub) and run

apt-get install ubuntu-desktop

---

### Post by m0pi on 2006-06-24
[QUOTE=paulyche]I can get into GDM, but gnome sessions crash with this error:

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /v ar/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "paul"
/etc/gdm/Xsession: Beginning session setup...
Failed to start message bus: Failed to read directory "/usr/local/share/dbus-1/services": No such file or directory
EOF in dbus-launch reading address from bus daemon

```

I can load a failsafe gnome session.
/usr/local/share/dbus-1/services doesn't exist,

but /usr/share/dbus-1/services does.

I don't know much about startup scripts but it seems they are pointing to the wrong thing, but I don't know why?

I'm a bit lost now.[/QUOTE]

I had the same problem.

> sudo gedit /etc/dbus-1/session.conf
Change :  > <servicedir>/usr/share/local/dbus-1/services</servicedir>
for :
> <servicedir>/usr/share/dbus-1/services</servicedir>

It happened after install XGL in my GDM session.

---

### Post by paulyche on 2006-06-25
Thanks m0pi.

Worked a treat. It was a rememant of me messing around with XGL.

---

