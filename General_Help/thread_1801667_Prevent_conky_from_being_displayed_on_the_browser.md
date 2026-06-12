---
title: "Prevent conky from being displayed on the browser"
date: 2011-07-10
forum: General Help
---

### Post by kanishkdudeja on 2011-07-10
How can i set conky to be only visible on the desktop?

not on the browser windows and the file windows?

My script is:

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
# 
 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 1.0
 
# Minimum size of text area
# minimum_size 250 5
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
 
# Stippled borders?
stippled_borders 3
 
# border margins
border_margin 9
 
# border width
border_width 10
 
# Default colors and also border colors, grey90 == #e5e5e5
default_color grey
 
own_window_colour brown
own_window_transparent yes
 
# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
 
# Gap between borders of screen and text
gap_x 10
gap_y 10
 
# stuff after 'TEXT' will be formatted on screen
 
TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine
 
${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
 
${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color
 
Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
Home:  ${fs_free_perc /media/Home}%   ${fs_bar 6 /media/Home}$color
 
${color orange}NETWORK (${addr ppp0}) ${hr 2}$color
Down: $color${downspeed ppp0} k/s ${alignr}Up: ${upspeed ppp0} k/s
${downspeedgraph ppp0 25,140 000000 ff0000} ${alignr}${upspeedgraph ppp0 
25,140 000000 00ff00}$color
Total: ${totaldown ppp0} ${alignr}Total: ${totalup ppp0}
${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}
 
${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}
```

---

### Post by Frogs Hair on 2011-07-10
I tried your script and it did not work , but I was not sure if it was complete . Try the code instead of "own_window_type override" .```
own_window_type desktop
``` If it doesn't work change it back.

---

### Post by wildmanne39 on 2011-07-10
Hi, also if you have not set your conky to startup after compiz by setting about a 30 second delay then it will cover your whole desktop.

---

### Post by kanishkdudeja on 2011-07-10
okay il try both the suggestions and will get back..:)

---

### Post by kanishkdudeja on 2011-07-11
Removed "own_window_type override" line.

It worked..

thanks guys..:)

---

### Post by Habitual on 2011-07-11
woo-hoo!

---

