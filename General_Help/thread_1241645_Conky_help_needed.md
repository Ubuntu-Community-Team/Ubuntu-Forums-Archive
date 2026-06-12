---
title: "Conky help needed"
date: 2009-08-16
forum: General Help
---

### Post by Chris-buntu on 2009-08-16
Hey guys, I just installed Ubuntu today, and I'm having troubles with conky.

It's installed fine, but when I run it, it runs in a Windowed mode, I don't want that, I just want it to sit on my desktop.

My conf file:

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#own_window_hints undecorated,below,skip_taskbar
background yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

maximum_width 143 5
minimum_size 143 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 4

# border margins
border_margin 2

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

#own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 2
gap_y 20

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 0}${color white}uptime: ${color }$uptime
${offset 0}${color white}kernel: ${color }$kernel
${offset 0}${color white}battery:${color } ${battery}
${offset 0}${color white}fan: ${ibm_fan}rpm
${offset 0}${color white}temp:
${offset 0}${color white} hda: ${hddtemp /dev/hda}
${offset 0}${color white} c1: ${ibm_temps 1}C
${offset 0}${color white} c2: ${ibm_temps 2}C
${offset 0}${color white} gpu: ${ibm_temps 3}C
${offset 0}${color white} cpu: ${ibm_temps 0}C
${offset 0}${color white}cpu:${color } $cpu%
${offset 0}${cpugraph 20,130 cccccc ffffff}
${offset 0}${color white}load: ${color }$loadavg
${offset 0}${color white}processes: ${color }$processes  
${offset 0}${color white}running: ${color }$running_processes

${offset 0}${color white}top cpu time:
${offset 0}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 0}${color white} ${top name 2}${top cpu 2}
${offset 0}${color white} ${top name 3}${top cpu 3}
${offset 0}${color white} ${top name 4}${top cpu 4}

${offset 0}${color white}top mem:
${offset 0}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 0}${color white} ${top_mem name 2}${top_mem mem 2}
${offset 0}${color white} ${top_mem name 3}${top_mem mem 3}
${offset 0}${color white} ${top_mem name 4}${top_mem mem 4}

${offset 0}${color white}ram:
${color }$memperc% $mem/$memmax
${offset 0}${membar 3,100}
${offset 0}${color white}swap:
${color }$swapperc% $swap/$swapmax
${offset 0}${swapbar 3,100}
${offset 0}${color white}root:
${color }${fs_free /}/${fs_size /}
${offset 0}${fs_bar 3,100 /}
${offset 0}${color white}net:
${offset 0}${color} wlan signal: ${color }${linkstatus eth1}%
${offset 0}${color} ip: ${addr eth1}
${offset 0}${color}up: ${color }${upspeed eth1} k/s
${offset 0}${upspeedgraph eth1 20,130 000000 ffffff}
${offset 0}${color}down: ${color }${downspeed eth1}k/s${color}
${offset 0}${downspeedgraph eth1 20,130 000000 ffffff}
```

Thank you for your help.

---

