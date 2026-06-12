---
title: "conky is causing xorg to use between 20-30% of CPU!"
date: 2011-02-10
forum: General Help
---

### Post by MiKOTRON on 2011-02-10
I'm not sure why it's doing this.  It's a big mystery. 

here's my .conkyrc
```
background yes
use_xft yes
xftfont HandelGotD:size=9
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 250 5
maximum_width 250
draw_shades no
draw_outline yes
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color black
alignment top_right
gap_x 12
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

TEXT
${color orange}SYSTEM ${hr 2} $color
$sysname $kernel $alignr $machine
Uptime $alignr $uptime
Load $alignr $loadavg
$processes processes ($running_processes running)

NAME${alignr}PID         CPU%        MEM%
${top name 1}${alignr}${top pid 1}       ${top cpu 1}          ${top mem 1}   
${top name 2}${alignr}${top pid 2}       ${top cpu 2}          ${top mem 2}   
${top name 3}${alignr}${top pid 3}       ${top cpu 3}          ${top mem 3}   
${top name 4}${alignr}${top pid 4}       ${top cpu 4}          ${top mem 4}

${color orange}Ethernet (${addr eth0}) ${hr 2} $color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 20,120 e5e5e5 F1AA0E} ${alignr}${upspeedgraph eth0
20,120 e5e5e5 F1AA0E}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}CPU ${hr 2} $color
${freq}MHz${alignr}Load: ${loadavg}
${alignr}${loadgraph 20,250 e5e5e5 F1AA0E}
CPU Total:${color} ${cpu cpu0}% ${color}${alignr}Temp:${color} ${execi 2 cat /sys/bus/pci/drivers/k8temp/000*/temp1_input | cut -c1,2 | awk '{print ($1*9)/5+32}'}${iconv_start UTF-8 ISO_8859-1}°F ${iconv_stop}
${alignr}${cpugraph 0 20,250 e5e5e5 F1AA0E}

${color orange}Memory ${hr 2} $color
RAM $mem / $memmax ${alignr}${membar 8,60}
Swap $swap / $swapmax ${alignr}${swapbar 8,60}

${color orange}HDD ${hr 2} $color
/ $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
${fs_bar /}

/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}

${color orange}Weather ${hr 2} $color ${execpi 600 sh /home/mike/conky_weather/weather_script.sh}
Today's Conditions
${font conkyweather:size=35}${execpi 600  sed -n '4p' /home/mike/conky_weather/weather1}${font}   ${voffset -20}${execpi 600 sed -n '1p' /home/mike/conky_weather/weather1}


${execpi 600 date --date="-1 days ago" '+%m/%d'}'s Forecast
${font conkyweather:size=35}${execpi 600  sed -n '5p' /home/mike/conky_weather/weather1}${font} ${alignr}${execpi 600 sed -n '2p' /home/mike/conky_weather/weather1| fold -w30}

${execpi 600 date --date="-2 days ago" '+%m/%d'}'s Forecast
${font conkyweather:size=35}${execpi 600  sed -n '6p' /home/mike/conky_weather/weather1}${font} ${alignr}${execpi 600 sed -n '3p' /home/mike/conky_weather/weather1| fold -w30}
```The first 2 screenshots are with conky running and the third one is without it running.

---

### Post by MiKOTRON on 2011-02-10
Okay, I changed
```
draw_outline yes
```
to
```
draw_outline no
```
in my .conkyrc

That setting it the processor hog. Huh...  Now the question is why and how to fix it?

---

### Post by MiKOTRON on 2011-02-11
-bump-

---

### Post by xdominex on 2011-04-23
Dude, I have this exact same problem. Not sure why this thread is being ignored, but it is unfortunate since Conky is the only reasonable choice for a system monitor, and I would like very much to be able to use it.

---

