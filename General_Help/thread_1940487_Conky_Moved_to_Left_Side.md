---
title: "Conky Moved to Left Side"
date: 2012-03-13
forum: General Help
---

### Post by Rodney9 on 2012-03-13
I re-started Xubuntu 11.10 and Conky that was always on the right side now has moved to the left side.

It doesn't make any difference changing .conkryc 

```
# Default Fonts
use_xft yes
xftfont Ubuntu:size=11
override_utf8_locale yes

# Performance Settings
update_interval 1
total_run_times 0
double_buffer yes
no_buffers yes
net_avg_samples 2
text_buffer_size 1024

# Window Settings
own_window no
own_window_transparent yes
own_window_type normal
own_window_argb_visual yes
own_window_argb_value 0
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Window border
draw_borders no
draw_shades no

# Default Color
default_color F5FFFA

# Color Title.
color0 FFFFE0

# Size and position
minimum_size 214 742
gap_x -90
gap_y -24
alignment top_right

TEXT

${GOTO 36}${font Ubuntu:bold:size=12}

${GOTO 36}${font Ubuntu:bold:size=36}${time %H:%M}  
${GOTO 36}${font Ubuntu:size=12}${time %A}, 
${GOTO 36}${time %d} ${time %B} ${time %Y}


${GOTO 36}${font Ubuntu:bold:size=12}System:

${GOTO 36}${font Ubuntu:size=12}${kernel}

${GOTO 36}CPU:${GOTO 100}${cpubar cpu1 10,75} ${cpu cpu1} %
${GOTO 36}RAM:${GOTO 100}${membar 10,75} ${memperc} %

${GOTO 36}Uptime:${GOTO 120}${uptime}

${GOTO 36}${font Ubuntu:bold:size=12}${color0}Disks${font}${color}

${GOTO 36}${font Ubuntu:size=12}System:${GOTO 120}${fs_used /}
${GOTO 36}${GOTO 60}${fs_bar 10,100 /}

${GOTO 36}${font Ubuntu:bold:size=12}${color0}Network${font}${color}

${GOTO 36}${font Ubuntu:size=12}Upspeed: ${GOTO 120}
${GOTO 36}${upspeed eth0}
${GOTO 36}${upspeedgraph eth0 10,75 B7B2AD B7B2AD}

${GOTO 36}Downspeed: 
${GOTO 36}${downspeed eth0} kb/s${GOTO 120}
${GOTO 36}${downspeedgraph eth0 10,75 B7B2AD B7B2AD}
${GOTO 36}Up:${GOTO 120}${totalup eth0}

${GOTO 36}Down:${GOTO 120}${totaldown eth0}
${GOTO 36}Local IP:${GOTO 120}${addr eth0}

```



Any Clues ?

Rodney

---

### Post by gordintoronto on 2012-03-13
Try:
alignment top_right

---

### Post by Rodney9 on 2012-03-13
> **gordintoronto said:**
> Try:
alignment top_right

Thank you, but that is what I have in .conkryc.

Rodney

---

### Post by wojox on 2012-03-14
Should work:
```
own_window yes
```

---

### Post by Rodney9 on 2012-03-14
> **wojox said:**
> Should work:
```
own_window yes
```

That fixed it, Thank You

Rodney

---

