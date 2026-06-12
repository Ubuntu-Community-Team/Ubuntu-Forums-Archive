---
title: "How to make Conky display &quot;stick&quot; in Lubuntu"
date: 2011-12-25
forum: General Help
---

### Post by M_Mynaardt on 2011-12-25
Hi there!

I'm slowly getting my desktop to look just the way I like it in the Lubuntu install on my laptop.  I just tried Conky.  And it *sort of* works.  It displays nicely; _until_ I click on the desktop and then my Conky display disappears.  Anyone know enough about Conky (and Lubuntu) to know why this is?

I'm probably overlooking something (almost) obvious in either some Lubuntu settings, or in my **[COLOR="DarkRed"].conkyrc[/COLOR]** file, which looks like this (based on the old Crunchbang one I had that worked well enough):
```
##############################################
#  Settings
##############################################
background yes
use_xft yes
xftfont sans:size=9
xftalpha 1
update_interval 1.0
total_run_times 0
own_window yes
own_window_transparent yes
own_window_type desktop
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 240 0
# original: minimum_size 200 200
maximum_width 240
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color d8d8d8
default_shade_color 000000
default_outline_color d9d7d6
alignment top_right
gap_x 12
gap_y 45
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
##############################################
#  Output
##############################################
TEXT
S Y S T E M    I N F O
${hr}
Host:$alignr$nodename
Uptime:$alignr$uptime
RAM:$alignr$mem/$memmax
$membar
# Swap usage:$alignr$swap/$swapmax
Disk usage:$alignr${fs_used /}/${fs_size /}
$fs_bar
CPU usage:$alignr${cpu cpu0}%
$cpubar

```

---

### Post by M_Mynaardt on 2011-12-30
Well!  A buddy of mine managed to fix my Conky problem.  He's better at Conky than I am, but it still took a bit of messing about to find the problem.

Just in case anyone else with Lubuntu is having the same problem I am, here's the trick...

In the **.conkyrc** file, make sure to comment out or delete the following line:
```
own_window_type desktop
```
If that line is in the **.conkyrc** file, then the Conky display will disappear when you click on anything in the desktop other than the Conky display itself.  Neither one of us know why that works in Lubuntu, but that's just the way it is!

:cool:

---

