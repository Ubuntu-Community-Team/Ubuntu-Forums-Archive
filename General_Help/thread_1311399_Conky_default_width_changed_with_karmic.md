---
title: "Conky default width changed with karmic"
date: 2009-11-02
forum: General Help
---

### Post by Tiberion on 2009-11-02
After an upgrade to karmic my conky is twice as wide.  I have posted my .conkyrc.  By the way I don't use borders.


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
update_interval 5.0
 
# Minimum size of text area
# minimum_size 250 5
 
# Draw shades?
draw_shades yes
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
 
# Stippled borders?
stippled_borders 3
 
# border margins
border_inner_margin 0
 
# border width
border_width 0
 
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
gap_x 5
gap_y 0
 
# stuff after 'TEXT' will be formatted on screen
 
TEXT
$color
${color gray}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine
 
${color gray}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${execi 1 sensors -f | grep -m1 "Core0 Temp:" | cut -d+ -f2 | cut -c1-7}
$cpubar 
${cpugraph 000000 00fff0}
${color gray}NAME            PID       CPU%      MEM%
${color red}${top name 1}   ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2}   ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3}   ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4}   ${top pid 4}   ${top cpu 4}    ${top mem 4}
 
${color gray}MEMORY / DISK ${hr 2}
${color sky blue}RAM:   $memperc% $mem/$memmax  ${membar 6}
${color royal blue}Swap:  $swapperc%   ${swapbar 6}$color
${color sky blue}HDD:    ${fs_used /}/ ${fs_size /}   ${fs_bar 6 /}$color 
 
${color gray}NETWORK (${addr wlan0}) ${hr 2}$color
Down: ${color yellow} ${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
$color${downspeedgraph wlan0 25,140 000000 ff0000} ${alignr}${upspeedgraph wlan0 
25,140 000000 00ff00}$color
${color ff0000}Total MB: ${totaldown wlan0} ${alignr}${color 00ff00}Total MB: ${totalup wlan0}
${color white}${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
${color gray}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}

---

### Post by TheFatHawaiian on 2009-11-10
I had the exact same issue as you. Here's a reply I got, though haven't tried this yet....stuck in work at the mo.

Hi,

The crux is in the following, had the same issue as you :smile:

# Minimum size of text area
#minimum_size 250 5
minimum_size 200 0
maximum_width 290 0

Adjust it to your liking.

cheers

---

### Post by manuti on 2009-11-11
same problem but ... it's ok the solution work for me:

[INDENT]# Minimum size of text area
minimum_size 200 0
maximum_width 300 0
[/INDENT]

---

### Post by Tiberion on 2009-11-11
Thanks for your help I appreciate it

---

