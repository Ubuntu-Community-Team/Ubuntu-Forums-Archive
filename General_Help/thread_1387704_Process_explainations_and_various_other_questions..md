---
title: "Process explainations and various other questions."
date: 2010-01-22
forum: General Help
---

### Post by Saiko Berry on 2010-01-22
:KS:KS:KS:KS:KS

Okay well I have some processes I'd like to know more about. It seems like most of this stuff has to do with kde imbred support and such but I'l list them anyways.

I run Karmic 9.10 2.6.31-17 generic kernel under and Openbox session.

Browser; uzbl/firefox

I don't think I run anything to do with kde, or any kde programs.. just KolourPaint If that is a KDE thing.

This is my Autostart just so you know. Im also confused about what power manager, keyring daemon etc load.. so that would be cool if people could shed light on that.

```
#!/bin/sh
. $GLOBALAUTOSTART
gnome-settings-daemon &
gnome-power-manager &
gnome-keyring-daemon &
xcompmgr &
(sleep 1 && wicd-client) &
(sleep 2 && tint2) &
(sleep 2 && pytyle) &
(sleep 17 && ~/.loadgraphs.sh) &
(sleep 20 && ~/Root/emesene-1.6/emesene) &
(sleep 20 && devilspie) &
(sleep 21 && urxvt) &
restricted-manager --check &
```The following are processes I'd like to be further explained. I know some of them like kio_file klauncher and such are for KDE programs but I don't really use KDE things so I'm concerned if these are removeable because I like a minimal system monitor. =3

```
dbus-daemon
dbus-launch
dcopserver [kdeinit] --nosid
gvfsd
gvfsd-http
gvfsd-fuse-daemon
gvfsd-gdu-volume-monitor
gvfsd-gphoto2-volume-monitor
kded2
kded [kdeinit] --new-startup
kdeinit4: kdeinit4 Running...
kdeinit Running...
kio_file
klauncher
klauncher [kdeinit] --new-startup
ssh-agent
```Also when I have userland trees open I have like 67 instances of console-kit-daemon.

Also when I run my dmenu script, to execute dmenu via this script;
```
#!/bin/sh
font='-dejavu-dejavu-medium-b-normal-*-*-120-100-100-m-0-iso8859-*'
background='#000000'
foreground='#D378B5'
selectedBackground='#D378B5'
selectedForeground='#000000'
$(dmenu_path | dmenu -i -p 'Saiko Terminal' -fn $font -nb $background -nf $foreground -sb $selectedBackground -sf $selectedForeground)
```When I run it, it runs twice instances and an instance or dmenu instead of just 1. What could be the cause of this? Also it seems sometimes it lingers a process so I can get 3 copies and a copy of dmenu running until I close it then 1 copy stays until I end the process.




Okay so long story short, Im confused and need some insight on a lot of things. :p

---

### Post by Saiko Berry on 2010-01-22
Anyone?

---

### Post by Saiko Berry on 2010-01-22
Seriously? Not one person on this forum can help?

---

### Post by Saiko Berry on 2010-01-23
... >.>

---

### Post by Saiko Berry on 2010-01-23
I refuse to believe nobody can help. :l

---

### Post by Saiko Berry on 2010-01-24
bump

---

