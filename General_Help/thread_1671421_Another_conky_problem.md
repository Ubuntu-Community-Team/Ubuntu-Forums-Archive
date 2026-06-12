---
title: "Another conky problem"
date: 2011-01-20
forum: General Help
---

### Post by GeissT on 2011-01-20
Hey,

Yet again I have another Conky problem.

Conky itself runs fine, its just when i log back in or reboot, it launches and is on top of all other windows and i have to restart conky to make it start normally.

Ive set it to start in the 'startup applications' feature. It starts with the command 'docky' no extra variables or expressions.

Here is my config:

```


alignment top_right
background no
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
use_xft yes
xftfont Comic Sans MS:size=10
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
double_buffer yes
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_transparent yes
own_window_class Conky
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no

```Any help is appreciated.

GeissT

---

### Post by Vaphell on 2011-01-20
try running it with a delay

```
sleep 20 && docky
``` (or whatever), create a script with that and try loading it in startup apps

---

### Post by GeissT on 2011-01-20
This solved my issue thanks.

:D GeissT

---

### Post by Quackers on 2011-01-20
This is my conky startup script
```
#!/bin/bash
sleep 30 && conky;
```
Try a semi colon after the docky

---

