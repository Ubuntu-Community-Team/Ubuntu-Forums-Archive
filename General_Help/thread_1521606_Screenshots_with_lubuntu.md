---
title: "Screenshots with lubuntu?"
date: 2010-07-01
forum: General Help
---

### Post by Oolongtea on 2010-07-01
How do I take a screenshot in lubuntu?

---

### Post by Oolongtea on 2010-07-01
I figured it out:

```
gnome-screenshot --delay 5
```

---

### Post by kerry_s on 2010-07-01
lubuntu uses scrot for screenshots. you can "man scrot" for the manual.

delay would be "scrot -d 5".

i'm guessing you installed gnome if you have gnome-screenshot.

---

### Post by cavalier911 on 2010-07-05
*mtPaint makes a lovely screenshot.*

Menu/Graphics/Grab screenshot

Copy/paste code to text file.
Save as **mtpaint-grab.desktop** to _/usr/share/applications _

```
[Desktop Entry]
Encoding=UTF-8
Name=Grab screenshot
Exec=mtpaint -s
Icon=/usr/share/icons/gnome/scalable/devices/camera.svg
Type=Application
Terminal=false
Categories=Application;Graphics;
```

---

### Post by pyrotechnician on 2010-11-01
@kerry_s
scrot is great for what i need.
thanx!

---

