---
title: "Conky won't stick to background"
date: 2009-10-12
forum: General Help
---

### Post by rmhamm on 2009-10-12
I can post my code if you want but basically conky won't stick to the background when I first boot up. It tries to treat conky like a regular window. It will cover any application until I kill it via terminal and then restart it.
Any insight?

---

### Post by VCoolio on 2009-10-12
Put it in a script with some delay so your window manager has the time to load. Call that script in startup applications. The script could look like this:
```
#!/bin/bash
sleep 30 && conky
```

Save where you want and in startup apps add 'sh /path/to/script'

---

### Post by OpenGuard on 2009-10-12
```
own_window yes

```

Do you have this in your conky config file ?

---

### Post by rmhamm on 2009-10-12
OpenGuard this is my .conkyrc it does contain own_window yes. I did get this code from another person but the regardless of the code this happens.

```
# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 4

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 180 0
#maximum_width 260

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
default_color grey
default_shade_color black

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35
gap_y 35

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

TEXT
SYSTEM ${hr 2}
${voffset 2}${font StyleBats:size=16}i${font}   Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}A${font}   CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
${font StyleBats:size=16}A${font}   CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
${font StyleBats:size=16}g${font}   RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font}   SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font StyleBats:size=16}q${font}   Uptime: ${alignr}${uptime}

DATE ${hr 2}
${alignc 17}${font Arial Black:size=16}${time %I:%M %P}${font}
${alignc}${time %A %d %B %Y}

HD ${hr 2}
${voffset 4}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Root:
${voffset 4}${fs_used /}/${fs_size /} ${alignr}${fs_bar 8,60 /}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home:
${voffset 4}${fs_used /home}/${fs_size /home} ${alignr}${fs_bar 8,60 /home}

NETWORK ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 BEBEBE BEBEBE}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,60 BEBEBE BEBEBE}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}Z${font}   Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr wlan0}
${else}${if_existing /proc/net/route eth0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth0}
${endif}${else}${if_existing /proc/net/route eth1}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth1}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth1}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth1}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Network Unavailable
${endif}

PROCESSES ${hr 2}
NAME $alignr PID    CPU
${top name 1} $alignr ${top pid 1} ${top cpu 1}
${top name 2} $alignr ${top pid 2} ${top cpu 2}
${top name 3} $alignr ${top pid 3} ${top cpu 3}
${top name 4} $alignr ${top pid 4} ${top cpu 4}
${top name 5} $alignr ${top pid 5} ${top cpu 5}
${top name 6} $alignr ${top pid 6} ${top cpu 6}
${top name 7} $alignr ${top pid 7} ${top cpu 7}
${top name 8} $alignr ${top pid 8} ${top cpu 8}
```

edited to add code tags

---

### Post by OpenGuard on 2009-10-12
Try this ..

```
# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 4

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar,skip_pager
own_window_transparent yes
own_window_type override

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 180 0
#maximum_width 260

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
default_color grey
default_shade_color black

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35
gap_y 35

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

TEXT
SYSTEM ${hr 2}
${voffset 2}${font StyleBats:size=16}i${font}   Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}A${font}   CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
${font StyleBats:size=16}A${font}   CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
${font StyleBats:size=16}g${font}   RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font}   SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font StyleBats:size=16}q${font}   Uptime: ${alignr}${uptime}

DATE ${hr 2}
${alignc 17}${font Arial Black:size=16}${time %I:%M %P}${font}
${alignc}${time %A %d %B %Y}

HD ${hr 2}
${voffset 4}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Root:
${voffset 4}${fs_used /}/${fs_size /} ${alignr}${fs_bar 8,60 /}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home:
${voffset 4}${fs_used /home}/${fs_size /home} ${alignr}${fs_bar 8,60 /home}

NETWORK ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 BEBEBE BEBEBE}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,60 BEBEBE BEBEBE}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}Z${font}   Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr wlan0}
${else}${if_existing /proc/net/route eth0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth0}
${endif}${else}${if_existing /proc/net/route eth1}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth1}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth1}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth1}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Network Unavailable
${endif}

PROCESSES ${hr 2}
NAME $alignr PID    CPU
${top name 1} $alignr ${top pid 1} ${top cpu 1}
${top name 2} $alignr ${top pid 2} ${top cpu 2}
${top name 3} $alignr ${top pid 3} ${top cpu 3}
${top name 4} $alignr ${top pid 4} ${top cpu 4}
${top name 5} $alignr ${top pid 5} ${top cpu 5}
${top name 6} $alignr ${top pid 6} ${top cpu 6}
${top name 7} $alignr ${top pid 7} ${top cpu 7}
${top name 8} $alignr ${top pid 8} ${top cpu 8}

```

---

### Post by rmhamm on 2009-10-12
no good. I tried the code and there was no change.

---

### Post by rmhamm on 2009-10-12
> **VCoolio said:**
> Put it in a script with some delay so your window manager has the time to load. Call that script in startup applications. The script could look like this:
```
#!/bin/bash
sleep 30 && conky
```

Save where you want and in startup apps add 'sh /path/to/script'

Tried but did not succeed. Only succeeded in slowing down my startup.

---

### Post by rmhamm on 2009-10-12
I added an attachment to show whats going on.[ATTACH]131750[/ATTACH]

---

### Post by VCoolio on 2009-10-13
try to play with the own_window_type, change it no normal for example. Options are normal, desktop and override (and dock if you have version 1.7.1 or higher).

---

### Post by wojox on 2009-10-13
```
own_window_transparent true
```

---

### Post by rmhamm on 2009-10-13
Both playing with own_window_type and own_window_transparency produced no results. Maybe it is because I'm running a 64 bit version of Ubuntu?
Should I file a bug report?

---

### Post by OpenGuard on 2009-10-13
> **rmhamm said:**
> Both playing with own_window_type and own_window_transparency produced no results. Maybe it is because I'm running a 64 bit version of Ubuntu?
Should I file a bug report?

[londonali1010]("http://ubuntuforums.org/member.php?u=779759") seems to be an expert in this field - give it a try .. she have a PM box too :P

---

### Post by KlinerDraken on 2009-10-13
try committing out own_window_hints
```
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

and setting draw_shades to no
```
draw_shades no
```

those are the only things i see different between yours and mine and mine works correctly. 

here is my conky file

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
draw_shades no

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
alignment top_right
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

TEXT
SYSTEM ${hr 2}
${voffset 2}${font OpenLogos:size=16}u${font}   Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}A${font}   CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
${font StyleBats:size=16}A${font}   CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
${font StyleBats:size=16}g${font}   RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font}   SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font StyleBats:size=16}q${font}   Uptime: ${alignr}${uptime}

DATE ${hr 2}
${alignc 35}${font Arial Black:size=26}${time %I:%M}${font} ${offset -4}${time %S}
${alignc}${time %A, %b %d %Y}

HARD DRIVES ${hr 2}
${voffset 4}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Root: ${alignr}${fs_size /}
${voffset 4}${fs_used /}/${fs_free /} ${alignr}${fs_bar 8,60 /}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home: ${alignr}${fs_size /home}
${voffset 4}${fs_used /home}/${fs_free /home} ${alignr}${fs_bar 8,60 /home}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Storage: ${alignr}${fs_size /media/Storage}
${voffset 4}${fs_used /media/Storage}/${fs_free /media/Storage} ${alignr}${fs_bar 8,60 /media/Storage}

NETWORK ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}Z${font}   Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr wlan0}
${else}${if_existing /proc/net/route eth2}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth2} kb/s ${alignr}${upspeedgraph eth2 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth2} kb/s ${alignr}${downspeedgraph eth2 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth2}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth2}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth2}
${endif}${else}${if_existing /proc/net/route eth1}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth1}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth1}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth1}
${endif}${else}${if_existing /proc/net/route eth0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth0}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Network Unavailable
${endif}

```

---

### Post by rmhamm on 2009-10-13
> **KlinerDraken said:**
> try committing out own_window_hints
```
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

and setting draw_shades to no
```
draw_shades no
```

those are the only things i see different between yours and mine and mine works correctly. 

here is my conky file

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
draw_shades no

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
alignment top_right
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

TEXT
SYSTEM ${hr 2}
${voffset 2}${font OpenLogos:size=16}u${font}   Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}A${font}   CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
${font StyleBats:size=16}A${font}   CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
${font StyleBats:size=16}g${font}   RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font}   SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font StyleBats:size=16}q${font}   Uptime: ${alignr}${uptime}

DATE ${hr 2}
${alignc 35}${font Arial Black:size=26}${time %I:%M}${font} ${offset -4}${time %S}
${alignc}${time %A, %b %d %Y}

HARD DRIVES ${hr 2}
${voffset 4}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Root: ${alignr}${fs_size /}
${voffset 4}${fs_used /}/${fs_free /} ${alignr}${fs_bar 8,60 /}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home: ${alignr}${fs_size /home}
${voffset 4}${fs_used /home}/${fs_free /home} ${alignr}${fs_bar 8,60 /home}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Storage: ${alignr}${fs_size /media/Storage}
${voffset 4}${fs_used /media/Storage}/${fs_free /media/Storage} ${alignr}${fs_bar 8,60 /media/Storage}

NETWORK ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}Z${font}   Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr wlan0}
${else}${if_existing /proc/net/route eth2}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth2} kb/s ${alignr}${upspeedgraph eth2 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth2} kb/s ${alignr}${downspeedgraph eth2 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth2}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth2}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth2}
${endif}${else}${if_existing /proc/net/route eth1}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth1}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth1}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth1}
${endif}${else}${if_existing /proc/net/route eth0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth0}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Network Unavailable
${endif}

```

Still not working. Could be a problem with my graphics card maybe? Pretty much grasping at straws here.

---

### Post by KlinerDraken on 2009-10-13
trying ending the conky process and running it from the terminal or form Alt+F2 and see if it is still over your other windows.

---

### Post by rmhamm on 2009-10-13
> **KlinerDraken said:**
> trying ending the conky process and running it from the terminal or form Alt+F2 and see if it is still over your other windows.

No that's how I get it to go away in the first place. I was looking for a solution to where I didn't have to do that.

---

### Post by KlinerDraken on 2009-10-13
> **rmhamm said:**
> No that's how I get it to go away in the first place. I was looking for a solution to where I didn't have to do that.

so when you do that it works correctly?

---

### Post by falconindy on 2009-10-13
> **rmhamm said:**
> No that's how I get it to go away in the first place. I was looking for a solution to where I didn't have to do that.
This is a problem that everyone has where Conky loads before the Window Manager (i.e. Compiz) and doesn't have the ability to do what you want at that point during the loading process. You've only got a few solutions:

1) write a shell script that delays conky's start until after the WM loads
2) find a WM that loads faster
3) load conky manually via alt-f2 or your favorite launcher

i'd personally go with #1.
```
#!/bin/bash
sleep 10
conky &
```
Is what I use.

---

### Post by proxess on 2009-10-14
Conky has to "wait" before starting so that Compiz starts, or else it becomes managed.

Like most people mentioned, create an executable script with the "sleep" command, and make it run on start up.

Also the options of the window make a difference. I don't know exactly what makes it behave properly, but I'm almost sure it's the own_window options:

```
own_window yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
own_window_transparent yes
own_window_type override
```

Here's an attachment of what it should look like.

---

### Post by stinkeye on 2009-10-14
Try this startup script from [_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=6809184&postcount=29[/COLOR]_]("http://ubuntuforums.org/showpost.php?p=6809184&postcount=29") 
if using compiz
[COLOR="Indigo"]**The Dbus plugin for compiz must be enabled.**[/COLOR]
```
#!/bin/bash
until [ "$done" = "true" ]
do
if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
then
DISPLAY=:0.0 conky -c *[COLOR="Blue"]/home/symlinked/Conky/conkymain[/COLOR]* >/dev/null 2>&1 &
#DISPLAY=:0.0 conky -c /home/symlinked/Conky/conkyclock >/dev/null 2>&1 &
#DISPLAY=:0.1 conky -c /home/symlinked/Conky/conkymain >/dev/null 2>&1 &
done="true";
else
echo "CONKY IS WAITING"
done="false"
sleep 5;
fi
done
exit 0
```
Change the highlighted part  to where your conky config is.
If you want to load more than one conky unhash the next line and change the path to your second conky config

This wont let conky load until compiz is fully functional.
Save to your conky folder or wherever you like, as startconky
Make executable...right click on file properties > permissions > tick executable box
Open startup applications 
add an entry 
name: conky       
Command:*/your path/to/location/*startconky

That should eliminate startup problems.
If that doesn't work you could try setting conky below in compiz.
CCSM > Window Management > Window Rules and type *Conky* in the below box.

p.s. This is what I have in my conky
```
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```
If you use "own_window_type overrride" it ignores "own_window_hints".
"own_window_type overrride" should still default to below, though.

Best thread for conky questions:
[_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=281865&page=983[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=281865&page=983")

---

### Post by falconindy on 2009-10-14
> **proxess said:**
> Conky has to "wait" before starting so that Compiz starts, or else it becomes managed.

Like most people mentioned, create an executable script with the "sleep" command, and make it run on start up.

Also the options of the window make a difference. I don't know exactly what makes it behave properly, but I'm almost sure it's the own_window options:

```
own_window yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
own_window_transparent yes
own_window_type override
```

Here's an attachment of what it should look like.
Nice (irrelevant) excuse to post your desktop that already got moderated once.

---

### Post by rmhamm on 2009-10-14
> **stinkeye said:**
> Try this startup script from [_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=6809184&postcount=29[/COLOR]_]("http://ubuntuforums.org/showpost.php?p=6809184&postcount=29") 
if using compiz
```
#!/bin/bash
until [ "$done" = "true" ]
do
if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
then
DISPLAY=:0.0 conky -c *[COLOR="Blue"]/home/symlinked/Conky/conkymain[/COLOR]* >/dev/null 2>&1 &
#DISPLAY=:0.0 conky -c /home/symlinked/Conky/conkyclock >/dev/null 2>&1 &
#DISPLAY=:0.1 conky -c /home/symlinked/Conky/conkymain >/dev/null 2>&1 &
done="true";
else
echo "CONKY IS WAITING"
done="false"
sleep 5;
fi
done
exit 0
```
Change the highlighted part  to where your conky config is.
If you want to load more than one conky unhash the next line and change the path to your second conky config

This wont let conky load until compiz is fully functional.
Save to your conky folder or wherever you like, as startconky
Make executable...right click on file properties > permissions > tick executable box
Open startup applications 
add an entry 
name: conky       
Command:*/your path/to/location/*startconky

That should eliminate startup problems.
If that doesn't work you could try setting conky below in compiz.
CCSM > Window Management > Window Rules and type *Conky* in the below box.

p.s. This is what I have in my conky
```
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```
If you use "own_window_type overrride" it ignores "own_window_hints".
"own_window_type overrride" should still default to below, though.

Best thread for conky questions:
[_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=281865&page=983[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=281865&page=983")

Thanks. That did the trick.
Thanks to everyone else as well that tried to help me figure this out.
It would be nice to have this as an option in the start up applications. A checkbox that says wait until window manager is up and running.

---

