---
title: "Openbox and conky autostart"
date: 2011-10-09
forum: General Help
---

### Post by J V on 2011-10-09
I'm running conky on openbox (conkyrc below) and am having some problems.

If I run conky from .xinitrc it starts up before openbox and shows up on top of all other windows, instead of below them.

If I run conky from .config/openbox/autostart.sh it starts up fine, as this is called after openbox starts up.

If I restart openbox (Rightclick menu > restart) conky is on top again.

The solution to the problem is to kill and restart conky.

Why does conky sit on top unless started after openbox?

```
######################
# - Conky settings - #
######################
update_interval 0.5
total_run_times 0
net_avg_samples 1
cpu_avg_samples 1

imlib_cache_size 0
double_buffer yes
no_buffers yes

#####################
# - Text settings - #
#####################
use_xft yes
xftfont Ubuntu:size=8
override_utf8_locale yes
text_buffer_size 2048

#############################
# - Window specifications - #
#############################
own_window_class Conky
own_window yes
own_window_type override
own_window_transparent yes
#own_window_argb_visual yes
#own_window_argb_value 100

alignment tr
gap_x 20
gap_y 0
minimum_size 391 1000


default_bar_size 80 8

#########################
# - Graphics settings - #
#########################
draw_shades no

default_color efefef
default_shade_color 1d1d1d
color0 ffffff
color1 ffffff
color2 ffffff


#lua_load ~/.conky/conkybg.lua
#lua_draw_hook_pre conky_draw_bg

TEXT

${font Ubuntu:size=20}${color1}${alignr}${time %A %B %d %Y}
${voffset -10}${font Ubuntu:size=16}${color1}${alignr}${offset -2}${time %H:%M:%S}
${voffset -12}${font Ubuntu:size=8}${color1}${alignr}${offset -5}${time %s}

${goto 180}${font Ubuntu:style=Bold:size=9}SYSTEM
${goto 180}${font}${color}VOLUME:${font Ubuntu:style=Bold:size=8}${color1}${goto 270}${execbar .conky/printvolume.sh bar} ${exec .conky/printvolume.sh}
${goto 180}${font}${color}CPU1:${font Ubuntu:style=Bold:size=8}${color1}${goto 270}${cpubar cpu1} ${cpu cpu1}%
${goto 180}${font}${color}CPU2:${font Ubuntu:style=Bold:size=8}${color1}${goto 270}${cpubar cpu2} ${cpu cpu2}%
${goto 180}${font}${color}RAM:${font Ubuntu:style=Bold:size=8}${color1}${goto 270}${membar} $memperc%
${goto 180}${font}${color}SWAP:${font Ubuntu:style=Bold:size=8}${color1}${goto 270}${swapbar} $swapperc%
${goto 180}${font}${color}UPTIME:${font Ubuntu:style=Bold:size=8}${color1}${goto 270}${uptime}

${goto 180}${font Ubuntu:style=Bold:size=9}NETWORK
${goto 180}${font}${color}External IP:${goto 270}${font Ubuntu:style=Bold:size=8}${color1}${execi 600 wget -O - http://whatismyip.org/ | tail}
${goto 180}${font}${color}Local IP:${goto 270}${font Ubuntu:style=Bold:size=8}${color1}${addr eth0}
${goto 180}${font}${color}Up:${goto 270}${font Ubuntu:style=Bold:size=8}${color1}${upspeed eth0}
${goto 180}${font}${color}Total up:${goto 270}${font Ubuntu:style=Bold:size=8}${color1}${totalup eth0}
${goto 180}${color}${font}Down:${goto 270}${font Ubuntu:style=Bold:size=8}${color1}${downspeed eth0}
${goto 180}${font}${color}Total down:${goto 270}${font Ubuntu:style=Bold:size=8}${color1}${totaldown eth0}

${goto 180}${font Ubuntu:style=Bold:size=9}TODO
${goto 190}${font}${color}${execi 10 cat todo}
${image ~/.conky/BG.png -p 170,95}
```

---

### Post by TeoBigusGeekus on 2011-10-09
Instead of just putting
```
conky
```
in either .xinitrc or autostart.sh, create a text file, put these lines
```
sleep 5
conky
```
in it, save it as conky_start in your home folder and put
/home/yourusername/conky_start in .xinitrc or autostart.sh.

---

### Post by J V on 2011-10-11
Yeah I just used:
```
(sleep 2s && conky)&
```

But I would still rather do it the less hacky way and find out *why* this is happening like this. Restarting openbox still makes conky on top.

---

### Post by TeoBigusGeekus on 2011-10-11
> **J V said:**
> Yeah I just used:
```
(sleep 2s && conky)&
```

But I would still rather do it the less hacky way and find out *why* this is happening like this. Restarting openbox still makes conky on top.

It's an old bug in conky; it's been there for as long as I've used it.

Try to increase the value in the sleep command from 2 to 5 or even 10.

---

