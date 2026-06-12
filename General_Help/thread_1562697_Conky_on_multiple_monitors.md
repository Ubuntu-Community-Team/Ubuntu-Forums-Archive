---
title: "Conky on multiple monitors"
date: 2010-08-28
forum: General Help
---

### Post by Floss on 2010-08-28
I have conky installed on Ubuntu 10.04.  I am using 2 monitors.  I want to have conky along the right side of the screen, but when the second monitor is on the it is on the right side of the second monitor.  I want to have conky display on the right side of the main monitor because the only thing I use the second monitor is for is to watch movies full screened.

---

### Post by Floss on 2010-08-28
bump

---

### Post by TeoBigusGeekus on 2010-08-28
Give a gap_x value to your conky script.
I.e., add a line
```
gap_x number
```
where number is the horizontal resolution of your second monitor.
EDIT: The above applies only if your alignment is configured as a right one (top right or bottom right).

---

### Post by Floss on 2010-08-28
I tried to use gap_x and nothing changed.  Should it be gap_x 1000 or gap_x 1000px or what?

---

### Post by TeoBigusGeekus on 2010-08-28
It should be 
```
gap_x 1000
```
Could you post your entire conkyrc?

---

### Post by Floss on 2010-08-28
Like this the conky just displays against the very right side still

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
border_inner_margin 9
 
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
gap_x 1500
 
# Gap between borders of screen and text
gap_x 10
gap_y 10
 
# stuff after 'TEXT' will be formatted on screen
 
TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname on $machine
Uptime: $uptime
 
${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}
# ${cpugraph 000000 ffffff}

Core 1: ${cpu cpu1}% ${cpubar cpu1}
Core 2: ${cpu cpu2}% ${cpubar cpu2}
Core 3: ${cpu cpu3}% ${cpubar cpu3}
Core 4: ${cpu cpu4}% ${cpubar cpu4}
 
${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $mem / $memmax   ${membar 6}$color
Swap:  $swap / $swapmax   ${swapbar 6}$color
 
Root:  ${fs_used /} / ${fs_size /}   ${fs_bar 6 /}$color
    Read: ${diskio_read /}  Write: ${diskio_write /}
Win 7: ${fs_used /srv/win7} / ${fs_size /srv/win7}   ${fs_bar 6 /srv/win7}$color
    Read: ${diskio_read /dev/sda1}  Write: ${diskio_write /dev/sda1}
Data RAID:  ${fs_used /srv/data} / ${fs_size /srv/data}   ${fs_bar 6 /srv/data}$color
    Read: ${diskio_read /dev/sdc2}  Write: ${diskio_write /dev/sdc2}
Backup:  ${fs_used /srv/backup} / ${fs_size /srv/backup}1   ${fs_bar 6 /srv/backup}$color
    Read: ${diskio_read /dev/sdb1}  Write: ${diskio_write /dev/sdb1}

${color orange}Processes ${hr 2}$color
Total Processes: $processes
Running Processes: $running_processes

NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
${top name 5} ${top pid 5}   ${top cpu 5}    ${top mem 5}
 
${color orange}NETWORK ${hr 2}$color
Public IP:  ${execi 3600 wget -O - http://whatismyip.org/ | tail}
eth0:         ${addr eth0}

Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
# ${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}

#${color orange}LOGGING ${hr 2}$color
#${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}
```

---

### Post by TeoBigusGeekus on 2010-08-28
```
...
# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
[COLOR="Red"]gap_x 1500[/COLOR]
 
# Gap between borders of screen and text
[COLOR="red"]gap_x 10[/COLOR]
gap_y 10
 
# stuff after 'TEXT' will be formatted on screen
 
TEXT
$color
...
```
You've set the gapx to 1500 and then to 10...
Delete the second gap_x command.

---

### Post by Floss on 2010-08-28
Ah thanks I didn't notice that.  That fixed it thank you.

---

### Post by TeoBigusGeekus on 2010-08-28
You're welcome.

---

