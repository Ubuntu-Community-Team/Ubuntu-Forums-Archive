---
title: "Desperately Need Help with Conky."
date: 2010-09-18
forum: General Help
---

### Post by GrantStoner on 2010-09-18
I've searched google endlessly - along with Ubuntu Forums - about Conky and how to get it to show the weather. A lot of different posts have instructions that use different scripts and whatnot from what another uses. Some even say they used conkyWeather or something that they added from a PPA source. Some have font scripts and such and have the weather pictures. I'm ok with plain text though either way. I've tried so many ways and failed, and I think I'm just getting confused on the different ways. At the bottom is a screenshot attachment. Here is my .conkyrc
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
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 1

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
# default_color brown (original default)
default_color 00ff00

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

# stuff after ‘TEXT’ will be formatted on screen

TEXT
$color
${color red}SYSTEM ${hr 2}$color

$nodename $sysname $kernel on $machine
${color 00ff00}${time %a, } ${color }${time %e %B %G}
${color 00ff00}Uptime:$color $uptime
CPU Temp: ${acpitemp}C
${color 00ff00}Battery${color 00ff00}:${color green} ${execibar 15 /home/grant/bat.pl}


${color red}CPU ${hr 2}$color

${freq}MHz Load: ${loadavg} Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ff0000}
NAME PID CPU% MEM%
${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

${color red}MEMORY / DISK ${hr 2}$color

RAM: $memperc% ${membar 6}$color
Swap: $swapperc% ${swapbar 6}$color

Root: ${fs_free_perc /}% ${fs_bar 6 /}$color
hda1: ${fs_free_perc /media/hda1}% ${fs_bar 6 /media/hda1}$color
hdb3: ${fs_free_perc /media/hdb3}% ${fs_bar 6 /media/hdb3}

${color red}NETWORK (${addr wlan0}) ${hr 2}$color

Down: $color${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,140 000000 ff0000} ${alignr}${upspeedgraph wlan0
25,140 000000 ff0000}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color red}LOGGING ${hr 2}$color

${execi 30 tail -n3 /var/log/messages | fold -w50}

${color red}FORTUNE ${hr 2}$color

${execi 120 fortune -s | fold -w50}It looks like another successfull day at TheHaxLab!

```

---

### Post by blueridgedog on 2010-09-18
This is what I use, is well supported and really works well:

[http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328)

---

### Post by bra|10n on 2010-09-18
+1
It is well supported and if you follow the installation step by step you are guaranteed success ;)

---

