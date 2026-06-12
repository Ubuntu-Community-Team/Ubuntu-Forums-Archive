---
title: "Help w/ Conky scripts"
date: 2009-07-12
forum: General Help
---

### Post by pilp4 on 2009-07-12
I have conky install and it is working fine but the problem is that when i try to install scripts, they dont work. I start conky in the terminal and it outputs
```

Conky: statfs '/media/sda1': No such file or directory
Conky: desktop window (14000a8) is subwindow of root window (c3)
Conky: window type - override
Conky: drawing to created window (0x3800001)
Conky: drawing to double buffer
Conky: statfs '/media/sda1': No such file or directory
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
sh: /home/phil/scripts/email.pl: Permission denied
sh: /home/phil/scripts/weather.pl: Permission denied
sh: /home/phil/scripts/torrent.pl: Permission denied
sh: /home/phil/scripts/torrent.sh: Permission denied

```

Thanks for any help!

---

### Post by mobilediesel on 2009-07-13
> **pilp4 said:**
> I have conky install and it is working fine but the problem is that when i try to install scripts, they dont work. I start conky in the terminal and it outputs
```

Conky: statfs '/media/sda1': No such file or directory
Conky: desktop window (14000a8) is subwindow of root window (c3)
Conky: window type - override
Conky: drawing to created window (0x3800001)
Conky: drawing to double buffer
Conky: statfs '/media/sda1': No such file or directory
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
sh: /home/phil/scripts/email.pl: Permission denied
sh: /home/phil/scripts/weather.pl: Permission denied
sh: /home/phil/scripts/torrent.pl: Permission denied
sh: /home/phil/scripts/torrent.sh: Permission denied

```

Thanks for any help!

We'll have to see your .conkyrc file in order to help.

---

### Post by pilp4 on 2009-07-13
Here it is...

```

# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
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
update_interval 3.0
 
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
hda1:  ${fs_free_perc /media/sda1}%   ${fs_bar 6 /media/sda1}$color
 
${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}

${color orange}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar /}


[B]${texeci 600 /home/phil/.scripts/email.pl}
${texeci 600 /home/phil/.scripts/weather.pl}
${execpi 1 /home/phil/.scripts/torrent.pl}
${execpi 1 /home/phil/.scripts/torrent.sh}[/B]
```

---

