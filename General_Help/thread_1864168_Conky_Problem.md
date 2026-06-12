---
title: "Conky Problem"
date: 2011-10-18
forum: General Help
---

### Post by d3fau1t on 2011-10-18
Something weird happened to my conky after an update. I'm using gnome-shell, and the area around the rectangle "window" that conky draws is all distorted. As well, the "Fortune" feature doesn't line up right, but spills all the way to the side of the "rectangle". 

Here's a pic:
[IMG]http://i53.tinypic.com/10cjn6b.png[/IMG]

And here's my conky config:
```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_outer_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

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

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }$kernel
${offset 240}${color slate grey}CPU:${color } $cpu%
${offset 240}${cpugraph 20,160 000000 ffffff}
${offset 240}${color slate grey}Load: ${color }$loadavg
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}BATTERY${hr 1}
${offset 240}${color lightgrey}Power:${alignr}${color}${acpiacadapter}
${offset 240}${color lightgrey}Status:${alignr}${color}${battery BAT0}
${offset 240}${color lightgrey}Time:${alignr}${color}${battery_time BAT0}

${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${alignr}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${alignr}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${alignr}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${alignr}${top cpu 4}

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${alignr}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${alignr}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${alignr}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${alignr}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,160}
${offset 240}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,160}

${offset 240}${color slate grey}DISK:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,160 /}

${offset 240}${color slate grey}FORTUNE ${hr 1}$color
${offset 240}${execi 3600 fortune -s | fold -w29}

${offset 240}${color slate grey}${hr 1}$color
```

Can anybody tell me how to fix this? I really liked conky before, but now it looks kind of silly.

---

### Post by d3fau1t on 2011-10-20
*bump*

---

