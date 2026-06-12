---
title: "conky removes desktop icons"
date: 2010-11-13
forum: General Help
---

### Post by dioxip on 2010-11-13
Hello!

I've just installed conky, and therefore I'm still pretty new to it. I found a nice script and modified it abit, but now when I run conky. My icons on the desktop gets invisible, and only display if I hover them.

Here is my conky config:
```
# 
# ~/.conkyrc-clock - an attractive, Elegant Brit-style desktop clock
# 

alignment       top_right
color0          e1e1e1
color1          e04613
default_color   ffffff
double_buffer   yes
draw_shades     no
font            DejaVu Serif-36
gap_x           20
gap_y           20
minimum_size    225
own_window      no
update_interval 3
use_xft         yes

TEXT
$alignr${time %H:%M}$color0${time %P}${font DejaVu Serif-12}
$color1${hr 3}$color
$alignr${time %A | %-d %B}

${voffset 0}${color3}${font GE Inspira:bold:size=9}Core 1${color1}${alignr}${cpu cpu1}%
${voffset 1}${color3}${font GE Inspira:bold:size=9}Core 2${color1}${alignr}${cpu cpu2}%
${voffset 1}${color3}${font GE Inspira:bold:size=9}RAM${color1}${alignr}${memperc}%


${font Arial:bold:size=10}${color ffffff}TOP PROCESSES $color1${hr 3}$color
${voffset 0}${color3}${font GE Inspira:bold:size=9}${top_mem name 2}${alignr}${top mem 2} %
${voffset 0}${color3}${font GE Inspira:bold:size=9}${top_mem name 3}${alignr}${top mem 3} %
${voffset 0}${color3}${font GE Inspira:bold:size=9}${top_mem name 4}${alignr}${top mem 4} %
${voffset 0}${color3}${font GE Inspira:bold:size=9}${top_mem name 5}${alignr}${top mem 5} %
${voffset 0}${color3}${font GE Inspira:bold:size=9}${top_mem name 6}${alignr}${top mem 6} %
```

I hope someone got an answer to this :)

---

### Post by stinkeye on 2010-11-13
Change
```
own_window  no
```
to 
```
own_window  yes
```

and add
```
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager
```

---

### Post by dioxip on 2010-11-13
Thank you, fixed it. But are there a way to remove the background shade. So it looks like a part of the wallpaper?

I have ```
draw_shades no
```

---

### Post by stinkeye on 2010-11-13
> **dioxip said:**
> Thank you, fixed it. But are there a way to remove the background shade. So it looks like a part of the wallpaper?

I have ```
draw_shades no
```

Are you using compiz or metacity?

---

### Post by stinkeye on 2010-11-13
If your using compiz.....
Open **compizconfig-settings-manager** and go to
Effects > Window decoration and change the box for **Shadow windows** 
to read```
(any) & !(class=Conky)
```



If your using Metacity....
alt + F2 and run gconf-editor
Navigate to /apps/metacity/general/compositing_manager
and untick.

While your there, make a bookmark if you need to turn on again.

Got to go. Good Luck.

---

### Post by dioxip on 2010-11-13
Thanks alot, the compiz thing worked! ;)

---

### Post by kingbilly on 2010-12-06
Thanks for the guide, just took advantage of it.

---

