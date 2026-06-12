---
title: "how to acheive universal opaqueness of panel?"
date: 2010-04-29
forum: General Help
---

### Post by justborn on 2010-04-29
hey guys, can anyone help me achieve universal transparency for the panel??

---

### Post by stinkeye on 2010-04-29
Go into the folder of the theme your using in ~/.themes
and change the name of panel-bg.png to panel-bg.bak.png
It's normally in the panel folder of your theme.

---

### Post by justborn on 2010-04-29
can anyone help get in there.....coz it's not a locally installable theme,ain't in ma home directory.....

---

### Post by Wobblybob on 2010-04-29
if it's one of the standard themes it will be in /usr/share/themes

---

### Post by justborn on 2010-04-29
/usr/themes/Ambiance/gtk-2.10 had three files [COLOR="Red"]gtkrc[/color] , [color="red"]panel_bg.png[/color] and [color="red"]panel_bg_30.png[/COLOR] .

i renamed [COLOR="Red"]panel_bg.png[/COLOR] to [COLOR="Blue"]panel_bg.bak.png[/COLOR] ,but still there is no difference....

---

### Post by justborn on 2010-04-30
help guys!

---

### Post by stinkeye on 2010-04-30
I just tried this on my lucid install using the ambiance theme and it works.
Have to restart panel though


```
killall gnome-panel
```
Will kill the panel and it will automatically restart.

---

### Post by justborn on 2010-04-30
i renamed the image and restarted the panel.but still some ares like the notification area,window-switcher & desk-swicher area are still not opaque.....

---

### Post by stinkeye on 2010-04-30
> **justborn said:**
> i renamed the image and restarted the panel.but still some ares like the notification area,window-switcher & desk-swicher area are still not opaque.....
The active window of the window list won't be transparent
neither will the
workspace switcher.
As for the clock, try removing and adding.

---

### Post by justborn on 2010-04-30
yeah, the clock is coz i have rgba support on....

but even after i disabled it the windows-switcher and the desk-switcher don't go opaque,where as in the case to simple theme like human(classic)they do......

---

### Post by justborn on 2010-04-30
n now i got one more problem the wallpaper in between the two paanel doesn't load,and trying to make any appearance changes freezes the desktop.

---

