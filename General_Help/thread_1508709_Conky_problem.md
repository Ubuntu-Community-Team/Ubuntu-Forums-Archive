---
title: "Conky problem"
date: 2010-06-13
forum: General Help
---

### Post by nestoras7 on 2010-06-13
Conky hides my desktop icons!
I ve installed it in the topright of the screen...
When it starts it hides my icons which are on the left side!
my conkyrc is this:
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
own_window no
own_window_hints undecorated,below,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

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
gap_y 20

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=10
xftalpha 0.8

TEXT

${offset 240}${color #ffccaa}UpTime: ${color }$uptime

${offset 240}${color #ffccaa}   CPU:${color } $cpu%  
                                                                        ${acpitemp}C
#${offset 240}${cpugraph 20,130 000000 ffffff}

${offset 240}${color #ffccaa}  MEM:  ${color }$memperc%
                                                                       $mem/$memmax
#${offset 240}${membar 3,100}    

#${offset 240}${color #ffccaa}NET: 
${offset 240}${color red}      UP: ${color }${upspeed eth0} k/s
${offset 240}${color green}DOWN: ${color }${downspeed eth0}k/s${color}

#${offset 240}${color #ffccaa}Highest CPU:
#${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
#${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
#${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
#${offset 240}${color lightgrey} ${top name 4}${top cpu 4}
${offset 240}${color #ffccaa}Highest MEM:
${offset 240}${color lightgrey} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
#${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
#${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}


```and my conky_start.sh is this:
```
#!/bin/bash
sleep 10 && conky;

```

---

### Post by nestoras7 on 2010-06-13
up!

---

