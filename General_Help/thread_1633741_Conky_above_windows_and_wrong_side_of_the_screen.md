---
title: "Conky above windows and wrong side of the screen"
date: 2010-11-29
forum: General Help
---

### Post by ShatPank on 2010-11-29
Very much as the Title suggests.
I have Conky running at startup, however my main problem is that it runs above any windows I have open, (see screenshot)  the other problem I have is that I'd prefer it to run on the right hand side of the screen.

Could someone please edit my Conky config file so it would do just that as I have no clue what I'm doing, I'm still quite new to Linux.

Thanks


```
# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 180 0
#maximum_width 200

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color white
#default_shade_color black
#default_outline_color white
own_window_colour white

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 30

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none
draw_graph_borders no
TEXT
${offset 33}${color 517DA0}${font INFECTED:size=20}hardcore
${voffset -10}${offset 14}${font Defused::bold:size=10}${kernel}
${voffset 5}${color 517DA0}${font Defused:size=8}Uptime: ${color 73A5E8}${alignr}${uptime}

${color 517DA0}CPU0: ${offset 6}${color 73A5E8}${cpu cpu0}% ${offset -6}${alignr}${cpubar cpu1 8,60}
${voffset 3}${color 517DA0}CPU1: ${offset 9}${color 73A5E8}${cpu cpu1}% ${offset -9}${alignr}${cpubar cpu2 8,60}
${voffset 3}${color 517DA0}RAM: ${offset 12}${color 73A5E8}$memperc% ${offset -12}${alignr}${membar 8,60}
${voffset 3}${color 517DA0}SWAP: ${offset 2}${color 73A5E8}$swapperc% ${offset -2}${alignr}${swapbar 8,60}
${offset 66}${color 517DA0}${font INFECTED:size=20}SDA${font}
${voffset 5}${color 517DA0}${font Defused:size=8}Root:
${voffset 3}${color 73A5E8}${fs_free /}/${fs_size /} 
${voffset 3}${fs_bar 10,180 /}
${voffset 8}${color 517DA0}Home:
${voffset 3}${color 73A5E8}${fs_free /home}/${fs_size /home} 
${voffset 3}${fs_bar 10,180 /home}

${voffset 50}
${offset 43}${color 517DA0}${font INFECTED:size=20}TOP CPU${font}
${voffset 10}${color 73A5E8}${font JUICE Bold:size=8}${top name 1}${alignr}${top cpu 1}
${top name 2}${alignr}${top cpu 2}
${top name 3}${alignr}${top cpu 3}
${top name 4}${alignr}${top cpu 4}
${top name 5}${alignr}${top cpu 5}
${top name 6}${alignr}${top cpu 6}
${top name 7}${alignr}${top cpu 7}
${top name 8}${alignr}${top cpu 8}
${offset 43}${color 517DA0}${font INFECTED:size=20}TOP MEM${font}
${voffset 10}${color 73A5E8}${font JUICE Bold:size=8}${top_mem name 1}${alignr}${top_mem mem 1}
${top_mem name 2}${alignr}${top_mem mem 2}
${top_mem name 3}${alignr}${top_mem mem 3}
${top_mem name 4}${alignr}${top_mem mem 4}
${top_mem name 5}${alignr}${top_mem mem 5}
${top_mem name 6}${alignr}${top_mem mem 6}
${top_mem name 7}${alignr}${top_mem mem 7}
${top_mem name 8}${alignr}${top_mem mem 8}
${voffset 30}${offset 37}${color 517DA0}${font INFECTED:size=20}NETWORK
${voffset -10}${color 517DA0}${font Defused:size=8}Down: 
${downspeedgraph eth0 30,70 517DA0 73A5E8}${color 73A5E8}${voffset -15}${alignr}${downspeed eth0} 


${color 517DA0}${font Defused:size=8}Up:  
${upspeedgraph eth0 30,70 517DA0 73A5E8}${color 73A5E8}${voffset -15}${alignr}${upspeed eth0}

${voffset 3}${color 517DA0}Local Ip: ${color 73A5E8}${alignr}${addr eth0}
${if_running audacious2}${voffset 2}${offset 33}${color 517DA0}${font INFECTED:size=20}Audacious
${voffset -10}${color 73A5E8}${font JUICE Bold:size=8}${exec audtool2 --current-song | cut -b-32}
${voffset 3}${alignr}${exec audtool2 --current-song-output-length} / ${exec audtool2 --current-song-length}
${endif}
```

---

### Post by WorMzy on 2010-11-29
```
# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
**_own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager_**

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 180 0
#maximum_width 200

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color white
#default_shade_color black
#default_outline_color white
own_window_colour white

# Text alignment, other possible values are commented
#alignment top_left
**_alignment top_right_**
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 30

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none
draw_graph_borders no
TEXT
${offset 33}${color 517DA0}${font INFECTED:size=20}hardcore
${voffset -10}${offset 14}${font Defused::bold:size=10}${kernel}
${voffset 5}${color 517DA0}${font Defused:size=8}Uptime: ${color 73A5E8}${alignr}${uptime}

${color 517DA0}CPU0: ${offset 6}${color 73A5E8}${cpu cpu0}% ${offset -6}${alignr}${cpubar cpu1 8,60}
${voffset 3}${color 517DA0}CPU1: ${offset 9}${color 73A5E8}${cpu cpu1}% ${offset -9}${alignr}${cpubar cpu2 8,60}
${voffset 3}${color 517DA0}RAM: ${offset 12}${color 73A5E8}$memperc% ${offset -12}${alignr}${membar 8,60}
${voffset 3}${color 517DA0}SWAP: ${offset 2}${color 73A5E8}$swapperc% ${offset -2}${alignr}${swapbar 8,60}
${offset 66}${color 517DA0}${font INFECTED:size=20}SDA${font}
${voffset 5}${color 517DA0}${font Defused:size=8}Root:
${voffset 3}${color 73A5E8}${fs_free /}/${fs_size /} 
${voffset 3}${fs_bar 10,180 /}
${voffset 8}${color 517DA0}Home:
${voffset 3}${color 73A5E8}${fs_free /home}/${fs_size /home} 
${voffset 3}${fs_bar 10,180 /home}

${voffset 50}
${offset 43}${color 517DA0}${font INFECTED:size=20}TOP CPU${font}
${voffset 10}${color 73A5E8}${font JUICE Bold:size=8}${top name 1}${alignr}${top cpu 1}
${top name 2}${alignr}${top cpu 2}
${top name 3}${alignr}${top cpu 3}
${top name 4}${alignr}${top cpu 4}
${top name 5}${alignr}${top cpu 5}
${top name 6}${alignr}${top cpu 6}
${top name 7}${alignr}${top cpu 7}
${top name 8}${alignr}${top cpu 8}
${offset 43}${color 517DA0}${font INFECTED:size=20}TOP MEM${font}
${voffset 10}${color 73A5E8}${font JUICE Bold:size=8}${top_mem name 1}${alignr}${top_mem mem 1}
${top_mem name 2}${alignr}${top_mem mem 2}
${top_mem name 3}${alignr}${top_mem mem 3}
${top_mem name 4}${alignr}${top_mem mem 4}
${top_mem name 5}${alignr}${top_mem mem 5}
${top_mem name 6}${alignr}${top_mem mem 6}
${top_mem name 7}${alignr}${top_mem mem 7}
${top_mem name 8}${alignr}${top_mem mem 8}
${voffset 30}${offset 37}${color 517DA0}${font INFECTED:size=20}NETWORK
${voffset -10}${color 517DA0}${font Defused:size=8}Down: 
${downspeedgraph eth0 30,70 517DA0 73A5E8}${color 73A5E8}${voffset -15}${alignr}${downspeed eth0} 


${color 517DA0}${font Defused:size=8}Up:  
${upspeedgraph eth0 30,70 517DA0 73A5E8}${color 73A5E8}${voffset -15}${alignr}${upspeed eth0}

${voffset 3}${color 517DA0}Local Ip: ${color 73A5E8}${alignr}${addr eth0}
${if_running audacious2}${voffset 2}${offset 33}${color 517DA0}${font INFECTED:size=20}Audacious
${voffset -10}${color 73A5E8}${font JUICE Bold:size=8}${exec audtool2 --current-song | cut -b-32}
${voffset 3}${alignr}${exec audtool2 --current-song-output-length} / ${exec audtool2 --current-song-length}
${endif}
```

These changes were already there, don't give up so easy next time. You just needed to read through the contents of the file. ;)

---

### Post by ShatPank on 2010-11-29
Thank you, I read at the beginning about the hash tag's and just didn't take it in.
I guess with being new to Linux I'm still assuming most things will be more difficult than they often are, I've found just installing themes to be a bit of a bugger occasionally, thank you again though :)

---

