---
title: "Conky overrides everything"
date: 2010-06-28
forum: General Help
---

### Post by ankit singh on 2010-06-28
I installed conky and my scripts are as follows

```
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
maximum_width 240
default_color white
default_shade_color 000000
default_outline_color 000000
alignment top_right
gap_x 7
gap_y 35
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

TEXT
${font Aerial:style=Bold:pixelsize=12}SYSTEM${font Sans Seriff:size=9} ${hr 1 }
Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg
Intel(R) Core(TM)2 Duo CPU @ 2.40GHz
CPU Usage: ${alignc} ${freq}MHz X 2  
${cpu cpu0}% ${alignr}${cpubar cpu0 5,170}
${hr 1}
${font Aerial:style=Bold:pixelsize=12}Cores:
${cpu cpu1}% ${alignr}${cpubar cpu1 5,170}
${cpu cpu2}% ${alignr}${cpubar cpu2 5,170}
${hr 1}
Disk I/O: ${diskio} ${alignr}
${diskiograph /dev/sda 25,200}
${hr 1}
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}
Swap: ${alignr}$swap/$swapmax
${swapbar 4}
${font Sans Seriff:pixelsize=49}${alignc}${time %H:%M}${font Sans Seriff:size=9}
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
${font Aerial:style=Bold:pixelsize=12}FILESYSTEM ${font Sans Seriff:size=9}${hr 1}
Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}
${hr 1}
${font Aerial:style=Bold:pixelsize=12}NETWORK ${font Sans Seriff:size=9}${hr 1}
IP: ${addr eth0} / ${execi 3600 wget -O - http://whatismyip.org/ | tail}
TCP Connections: ${tcp_portmon 1 65535 count}
Down: ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107 cccccc 0000a3} ${alignr}${upspeedgraph eth0 25,107 cccccc 0000a3}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}
```

the problem is it overrides every thing.See the image below.But this problems solves when i restart conky but it again resurfaces
after reboot/logout, please help guys.

---

### Post by Smart Viking on 2010-06-28
How does it get launched at startup?

You might use something like this and add it to startup applications:

```
sleep 15; conky
```

I hope this helps. :)

---

### Post by glennzo on 2010-06-28
Here's the relevant portion of my config with things working as they should.
```
# --- Window Layout & Options --- #
own_window yes
own_window_colour brown
own_window_transparent yes
#own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
use_spacer right
use_xft yes
alignment top_right
gap_x 10
gap_y 40

# --- Colours, Sizes, Fonts & Margins --- #
update_interval 2.0
maximum_width 270
stippled_borders 3
border_margin 9
border_width 10
default_color grey

```

---

### Post by ankit singh on 2010-06-28
i have already added it to start up application.The problem is it overrides every window (in the above image)

---

### Post by Smart Viking on 2010-06-28
> **ankit singh said:**
> i have already added it to start up application.The problem is it overrides every window (in the above image)

Does it have delay? (sleep xx)

Because i have heard that can cause problems, to add it to startup applications without delay. Sorry if you already have it but if you do not, that can be the source of your problem. :)

---

### Post by ankit singh on 2010-06-30
Solved,yes my problem was that i forgot to delay it.

---

