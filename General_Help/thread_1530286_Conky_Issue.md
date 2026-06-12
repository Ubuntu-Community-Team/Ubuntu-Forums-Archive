---
title: "Conky Issue"
date: 2010-07-13
forum: General Help
---

### Post by Automag05 on 2010-07-13
Hi guys, I have been wanting conky to run at start up... fortunately I got that part done (I am very new) but after that, even though my conky was not configured to stand on top of my applications it would, and I didn't want that so I added some more code, and now it disappears if I click over it, it is still running, just not visible. If any one has a suggestion what  I should do with the conky script I would be appreciative! Here is my code...

 # UBUNTU-CONKY

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_type desktop
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes
xftfont Hemi head 426:size=9
xftalpha 0.8

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 200 10

# Maximum width
maximum_width 250

# Default color
default_color gray

# Text alignment, other possible values are commented
alignment top_right

# Gap between borders of screen and text
gap_x 12
gap_y 42

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${alignr}${color gray}${time %a, } ${color gray}${time %b %e - } ${color gray}${time %I:%M %p}
${color gray}SYSTEM ${hr 2}$color
Name: $nodename
Kernel: $sysname $kernel

${color gray}CPU ${hr 2}$color
Uptime: ${uptime}
${freq_g}GHz Load: ${loadavg}
${cpugraph gray ffffff}
PROCESS NAME${alignr}CPU%
${top name 1}${alignr}${top cpu 1}
${top name 2}${alignr}${top cpu 2}
${top name 3}${alignr}${top cpu 3}
${top name 4}${alignr}${top cpu 4}
${top name 5}${alignr}${top cpu 5}

${color gray}MEMORY${hr 2}$color
RAM:$alignr$mem/$memmax
RAM: $memperc% ${membar 6}$color
Swap: $swapperc% ${swapbar 6}$color

MEMORY NAME${alignr}MEM %
${top_mem name 1}${alignr}${top_mem mem 1}
${top_mem name 2}${alignr}${top_mem mem 2}
${top_mem name 3}${alignr}${top_mem mem 3}
${top_mem name 4}${alignr}${top_mem mem 4}
${top_mem name 5}${alignr}${top_mem mem 5}

${color gray}DISK SPACE USED${hr 2}$color
Root: ${fs_used_perc /}%${alignr}${fs_used /} / ${fs_size /}
Home: ${fs_used_perc /home}%${alignr}${fs_used /home} / ${fs_size /home}
DATA: ${fs_used_perc /mnt/data}%${alignr}${fs_used /mnt/data} / ${fs_size /mnt/data}

${color gray}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 18,100 000000 green} ${alignr}${upspeedgraph eth0 18,100 000000 green}$color

Thanks guys!

---

### Post by ankit singh on 2010-07-13
type a script and save it with the a name conky.sh in any folder u want.The script should contain the following code

```

#!/bin/bash
sleep 30
conky &
exit 0


```Right click on the file.Select properties->permissions->mark executable. Now open up System->Preference->start up application

In that search for conky(if it is not there then add a conky entry).After selecting conky,select the edit option and edit the command.The command here should be the location of the above script.Click ok.and reboot your pc.

I have given a detail "how to" [SIZE=5]at the bottom of the page[/SIZE]

[http://ubuntuforums.org/showthread.php?p=9554176#post9554176](http://ubuntuforums.org/showthread.php?p=9554176#post9554176)

---

### Post by nitstorm on 2010-07-13
> own_window_type override
own_window_type desktop

I am guessing the problem lies there... if u want ur conky to stay on top of all other windows at all times use  ***own_window_type override*** and delete the own_window_type desktop

and if u want it only on the desktop and not over the other windows or disappearing wen u click it delete both those lines and put these lines  
[I][B]own_window_type normal
background yes


[/B][/I]

---

### Post by ankit singh on 2010-07-13
My .conkyrc scripts are

> 
background yes
font Sans Seriff:size=9
xftfont Sans Seriff:size=9
use_xft yes
xftalpha 0.1
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 206 5
maximum_width 206
default_color e6df7e
default_shade_color 000000
default_outline_color 000000
alignment top_right
gap_x 6
gap_y 35
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

TEXT
${font Aerial:style=Bold:pixelsize=12}SYSTEM${font Vibrocentric:size=10} ${hr 1 }
Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg
Intel(R) Core(TM)2 Duo CPU E4600 @ 2.40GHz
CPU Usage: ${alignc} ${freq}MHz X 2  
${cpu cpu0}% ${alignr}${cpubar cpu0 5,170}
${hr 1}
Cores:
${cpu cpu1}% ${alignr}${cpubar cpu1 5,170}
${cpu cpu2}% ${alignr}${cpubar cpu2 5,170}
${hr 1}
Disk I/O: ${diskio} ${alignr}
${diskiograph /dev/sda 25,200}
${hr 1}
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}
${font Vibrocentric:pixelsize=49}${alignc}${time %H:%M}${font Vibrocentric:size=10}
Highest CPU $alignr CPU% MEM%
${hr 1}
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${hr 1}
Highest MEM $alignr CPU% MEM%
${hr 1}
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${hr 1}
${font Aerial:style=Bold:pixelsize=12}FILESYSTEM ${font Vibrocentric:size=10}${hr 1}
Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}
${hr 1}
${font Aerial:style=Bold:pixelsize=12}NETWORK ${font Vibrocentric:size=10}${hr 1}
Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107 cccccc e6df7e} ${alignr}${upspeedgraph eth0 25,107 cccccc e6df7e}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}


Note::p=":p"

---

### Post by Automag05 on 2010-07-13
[QUOTE=
```

#!/bin/bash
sleep 30
conky &
exit 0


```Right click on the file.Select properties->permissions->mark executable. Now open up System->Preference->start up application

[/QUOTE]

This worked perfectly for me, thank you guys for all your help... conky is odd, I have it installed on multiple computers, yet it act different on all them :)

---

