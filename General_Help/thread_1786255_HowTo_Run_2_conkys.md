---
title: "HowTo: Run 2 conkys"
date: 2011-06-19
forum: General Help
---

### Post by Robert Finley on 2011-06-19
I know a lot has been written on this subject. I have been experimenting a couple days now.  What I am trying to accomplish is to have a hardware monitor in the upper right of my screen and an RSS reader in the bottom left.

I have a script I like for the harware monitor.  /home/robert/.conkyrc I can make it work by itself just fine.
I haven't got the other script developed yet but I will figure it out.  For now, I'm just trying to use the same script with different name and screen placement. /home/robert/.conkyrss

The only difference between the 2 is this: conkyrc = 

background yes
use_xft yes
xftfont Sans:size=8
xftalpha 1
update_interval 1.0
total_run_times 0
own_window yes
own_window_transparent yes
own_window_type desktop
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 200
maximum_width 200
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color white
alignment top_right
gap_x 12
gap_y 60
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

TEXT
${font sans-serif:bold:size=8}SYSTEM ${hr 2}
${font sans-serif:normal:size=8}$sysname $kernel $alignr $machine
Host:$alignr$nodename
Uptime:$alignr$uptime
File System: $alignr${fs_type}

${font sans-serif:bold:size=8}PROCESSORS ${hr 2}
${font sans-serif:normal:size=8}${cpugraph cpu1}
CPU1: ${cpu cpu1}% ${cpubar cpu1}

${font sans-serif:bold:size=8}MEMORY ${hr 2}
${font sans-serif:normal:size=8}RAM $alignc $mem / $memmax $alignr $memperc%
$membar

${font sans-serif:bold:size=8}DISKS ${hr 2}
${font sans-serif:normal:size=8}/ $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_used_perc /}%
${fs_bar /}
SWAP $alignc ${swap} / ${swapmax} $alignr ${swapperc}%
${swapbar}

${font sans-serif:bold:size=8}TOP PROCESSES ${hr 2}
${font sans-serif:normal:size=8}${top_mem name 1}${alignr}${top mem 1} %
${top_mem name 2}${alignr}${top mem 2} %
$font${top_mem name 3}${alignr}${top mem 3} %
$font${top_mem name 4}${alignr}${top mem 4} %
$font${top_mem name 5}${alignr}${top mem 5} %

${font sans-serif:bold:size=8}NETWORK ${hr 2}
${font sans-serif:normal:size=8}IP address: $alignr ${addr eth0}
${downspeedgraph eth0}
DLS:${downspeed eth0} kb/s $alignr total: ${totaldown ath0}
${upspeedgraph eth0}
ULS:${upspeed eth0} kb/s $alignr total: ${totalup ath0}

conkyrss = the same with "alignment bottom_right"

Launching with /home/robert/.conky_start.sh which looks like this:

#!/bin/bash
sleep 60 &&
conky -c ~/home/robert/.conkyrc &
sleep 60 &&
conky -c ~/home/robert/.conkyrss &

When I boot, I only get the hardware monitor in the upper right and it disappears the first time I click on the desktop.

What am I doing wrong?

---

