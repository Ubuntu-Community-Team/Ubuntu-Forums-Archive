---
title: "Possible Conky Problem"
date: 2010-11-18
forum: General Help
---

### Post by Torombolo on 2010-11-18
My Desktop icons disappear, and the only thing that i think off is conky. since it started after it installed it.


Running Ubuntu 10.04


This is my conky file

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
own_window Desktop
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
draw_shades yes

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
gap_y 10

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset -850}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset -850}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset -850}${color slate grey}UpTime: ${color }$uptime
${offset -850}${color slate grey}Kern:${color }$kernel
${offset -850}${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${offset -850}${cpugraph 20,130 000000 ffffff}
${offset -850}${color slate grey}Load: ${color }$loadavg
${offset -850}${color slate grey}Processes: ${color }$processes  
${offset -850}${color slate grey}Running:   ${color }$running_processes

${offset -850}${color slate grey}Highest CPU:
${offset -850}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset -850}${color lightgrey} ${top name 2}${top cpu 2}
${offset -850}${color lightgrey} ${top name 3}${top cpu 3}
${offset -850}${color lightgrey} ${top name 4}${top cpu 4}

${offset -850}${color slate grey}Highest MEM:
${offset -850}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset -850}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset -850}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset -850}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset -850}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset -850}${membar 3,100}
${offset -850}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset -850}${swapbar 3,100}

${offset -850}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset -850}${fs_bar 3,100 /}
${offset -850}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset -850}${fs_bar 3,100 /home}
${offset -850}${color slate grey}NET: 
${offset -850}${color}Up: ${color }${upspeed wlan0} k/s
${offset -850}${upspeedgraph wlan0 20,130 000000 ffffff}
${offset -850}${color}Down: ${color }${downspeed wlan0}k/s${color}
${offset -850}${downspeedgraph wlan0 20,130 000000 ffffff}
```

---

### Post by VCoolio on 2010-11-18
Read [this](http://conky.sourceforge.net/faq.html), question nr. 5; like it says, also try 'normal' or 'override' or (in the newer conky versions) 'dock' or 'panel'. From the [manual](http://conky.sourceforge.net/config_settings.html): ```
if own_window is yes, you may specify type normal, desktop, dock, panel or override 
(default: normal). Desktop windows are special windows that have no window decorations; 
are always visible on your desktop; do not appear in your pager or taskbar; and are sticky 
across all workspaces.Panel windows reserve space along a desktop edge, just like panels 
and taskbars, preventing maximized windows from overlapping them. The edge is chosen based 
on the alignment option. Override windows are not under the control of the window manager. 
Hints are ignored. This type of window can be useful for certain situations. 
```

---

### Post by a-user on 2010-11-18
vcoolio, you had the right intension, but i do not see anything within your quoting that answers the te question.

but to do so: i guess your icons are under the conky window. i think you have it set to overide. well if you want your icons visible use normal. but in this case even with sticky etc. when you minimize all windows (view desktop command) conky gets minimized too.

so either live wih not viisble (but clickable) icons under the conky window or with minized conky when you execute the show desktop command.

---

### Post by stinkeye on 2010-11-19
Try this version of your config with numerous changes.
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
own_window_type normal
own_window_hints undecorated,below,skip_taskbar,skip_pager,sticky
own_window_transparent yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
minimum_size 180 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins


# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

own_window_colour brown


# Text alignment, other possible values are commented
#alignment tl
alignment tr
#alignment bl
#alignment br

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale yes
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${color slate grey}${time %a, } ${color }${time %e %B %G}
${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${color slate grey}UpTime: ${color }$uptime
${color slate grey}Kern:${color }$kernel
${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${cpugraph 20 000000 ffffff}
${color slate grey}Load:${alignr 2}${color }$loadavg
${color slate grey}Processes:${alignr 2}${color }$processes  
${color slate grey}Running:${alignr 2}${color }$running_processes

${color slate grey}Highest CPU:
${color #ddaa00} ${top name 1}${alignr 2}${top_mem cpu 1}
${color lightgrey} ${top name 2}${alignr 2}${top cpu 2}
${color lightgrey} ${top name 3}${alignr 2}${top cpu 3}
${color lightgrey} ${top name 4}${alignr 2}${top cpu 4}

${color slate grey}Highest MEM:
${color #ddaa00} ${top_mem name 1}${alignr 2}${top_mem mem 1}
${color lightgrey} ${top_mem name 2}${alignr 2}${top_mem mem 2}
${color lightgrey} ${top_mem name 3}${alignr 2}${top_mem mem 3}
${color lightgrey} ${top_mem name 4}${alignr 2}${top_mem mem 4}

${color slate grey}MEM:  ${color } $memperc% ${alignr 2}$mem/$memmax
${membar 3}
${color slate grey}SWAP: ${color }$swapperc% ${alignr 2}$swap/$swapmax
${swapbar 3}

${color slate grey}ROOT:    ${color }${alignr 2}${fs_free /}/${fs_size /}
${fs_bar 3 /}
${color slate grey}HOME:  ${color }${alignr 2}${fs_free /home}/${fs_size /home}
${fs_bar 3 /home}
${color slate grey}NET: 
${color}Up: ${color }${upspeed wlan0} k/s
${upspeedgraph wlan0 20 000000 ffffff}
${color}Down: ${color }${downspeed wlan0}k/s${color}
${downspeedgraph wlan0 20 000000 ffffff}
```

---

### Post by Torombolo on 2010-11-20
I think its working, but how can i move it to the other side of the Screen (<--) :)!


So far no problems with icons going away.

---

### Post by stinkeye on 2010-11-20
> **Torombolo said:**
> I think its working, but how can i move it to the other side of the Screen (<--) :)!


So far no problems with icons going away.

This section determines where it is displayed on the screen.
```
# Text alignment, other possible values are commented
#alignment tl
alignment tr
#alignment bl
#alignment br

# Gap between borders of screen and text
gap_x 10
gap_y 10
```

If you put it on the top left, conky will cover your desktop icons.


Type in the terminal
```
man conky
```
to see an explanation of all the variables.
eg alignment tr = top right.

---

