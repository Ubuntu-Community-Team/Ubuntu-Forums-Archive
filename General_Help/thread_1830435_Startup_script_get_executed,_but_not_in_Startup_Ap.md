---
title: "Startup script get executed, but not in Startup Applications"
date: 2011-08-21
forum: General Help
---

### Post by intheflesh on 2011-08-21
Hey guys, I have a problem...

I wanted to tweak mouse acceleration in Gnome, and I found out how. I made a script with following contents:
```
#!/bin/sh
xinput --set-prop "Logitech USB Optical Mouse" "Device Accel Constant Deceleration" 1
xinput --set-prop "Logitech USB Optical Mouse" "Device Accel Velocity Scaling" 1

```That was some time ago. It works, it gets executed (after panels finish loading), but I don't remember how/from where. It's not in Startup Applications. So, where can it be?

---

### Post by WyleECoyote on 2011-08-21
maybe in /etc/init.d or /etc/rc* folders

---

### Post by intheflesh on 2011-08-21
@WyleECoyote: Yep, that's what Im grepping for right now.

```
sudo grep -r --exclude-dir="/data1" --exclude-dir="/data2" --exclude-dir="/windows" "Device Accel" *

```/data1, /data2 and /windows are automounted ntfs partitions...

This should be over like, next thursday...

---

### Post by ajgreeny on 2011-08-21
It may also be in /etc/rc.local, though that will be executed before the xsession, so probably not be the most likely place.

---

### Post by intheflesh on 2011-08-21
Well, it gets executed only after I've logged on. It's still unchanged at gdm login screen. Is there any place else except Startup Applications (gnome-session-properties) that can a script be put in to start with Gnome?

---

### Post by intheflesh on 2011-08-21
Khm... nothing gets executed. I ran gnome-mouse-properties as gdm:
```

xhost +SI:localuser:gdm
sudo -u gdm dbus-launcher gnome-mouse-properties

```and set both values to lowest, and there was no difference between mouse movement in gdm and Gnome. So I went to
```
/etc/gdm/Init/Default
```and added
```

xinput --set-prop "Logitech USB Optical Mouse" "Device Accel Constant Deceleration" 2
xinput --set-prop "Logitech USB Optical Mouse" "Device Accel Velocity Scaling" 1

```just before exit 0 and got what I wanted in gdm. I then made
```
/etc/gdm/PostLogin/Default
```and wrote the same. Now I have it in Gnome, too. Just got to check out whether it's present in Openbox.

---

