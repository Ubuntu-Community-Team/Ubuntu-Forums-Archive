---
title: "How to use full length of screen for Conky"
date: 2010-10-08
forum: General Help
---

### Post by avacomputers on 2010-10-08
I am trying to get conky to use the whole length of the screen instead of just have.

This is my conky file. PLease help.

```
Conky 2

background yes
use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color green
default_shade_color red
default_outline_color green
alignment top_right
gap_x 18
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale no
use_spacer yes

TEXT
$sysname $kernel $alignr $machine
Intel Centrino Duo $alignr${freq_g cpu0}Ghz
Uptime:$alignr$uptime
${time %A}$alignr${time %F}
$alignr
${cpugraph cpu0 16,200 ffffff ffffff}
CPU:1  ${cpu cpu1}% ${cpubar cpu1}
CPU:2  ${cpu cpu2}% ${cpubar cpu2}
MEM $alignc $mem / $memmax $alignr $memperc%
$membar
/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}
/fat $alignc ${fs_used /media/fat} / ${fs_size /media/fat} $alignr ${fs_free_perc /media/fat}%
${fs_bar /media/fat}
Disk i/o ${diskiograph 16,200} 
Processes 
$alignr $running_processes Running 
$alignr $processes Sleeping
Top Processes
CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 2}${top mem 3}
MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}
IP on eth1 $alignr ${addr eth1}
Down $alignr ${downspeed eth1} kb/s
${downspeedgraph eth1}
Up $alignr ${upspeed eth1} kb/s
${upspeedgraph eth1 16,200}
Connections ${tcp_portmon 32768 61000 count} ${alignr} Service/Port
${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}

email
${texeci 120 python ~/.gmail/gmail.py  | ~/.gmail/conkyhelper.rb }
phaed.one@gmail.com: $alignr ${if_existing /tmp/.gmailnew}$endif${exec cat /tmp/.gmailcount} New
phaedrus@cia.com: $alignr 0 New
```

---

### Post by avacomputers on 2010-10-08
Nevermind. I got it.

---

