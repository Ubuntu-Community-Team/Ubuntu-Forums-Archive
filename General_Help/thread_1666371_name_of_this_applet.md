---
title: "name of this applet?"
date: 2011-01-13
forum: General Help
---

### Post by camaron1 on 2011-01-13
Does anyone know the name of the volume applet (package) shown in the screen shot? I want to remove it. I'm on 10.10 and it appears every time I switch sound output from the SoundMenu.


Thanks in advance

---

### Post by hhh on 2011-01-13
I'm not sure, as I use Xfce and not Gnome, but try indicator-sound .

---

### Post by camaron1 on 2011-01-18
> **hhh said:**
> I'm not sure, as I use Xfce and not Gnome, but try indicator-sound .

Thanks, that actually removes the new soundmenu which is the one I want to keep.

Any more ideas?

---

### Post by stinkeye on 2011-01-18
gnome-volume-control-applet

It's the old style volume control that shows in the notification area.
Included in the **gnome-media** package.

You could make it non-executable with
```
sudo chmod -x /usr/bin/gnome-volume-control-applet
```


If that causes problems with your sound, change back with
```
sudo chmod +x /usr/bin/gnome-volume-control-applet
```

---

### Post by camaron1 on 2011-01-19
> **stinkeye said:**
> gnome-volume-control-applet

It's the old style volume control that shows in the notification area.
Included in the **gnome-media** package.

You could make it non-executable with
```
sudo chmod -x /usr/bin/gnome-volume-control-applet
```


If that causes problems with your sound, change back with
```
sudo chmod +x /usr/bin/gnome-volume-control-applet
```

Thanks stinkeye, that did the job

---

