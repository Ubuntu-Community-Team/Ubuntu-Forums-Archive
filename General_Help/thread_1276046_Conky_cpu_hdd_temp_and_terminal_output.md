---
title: "Conky cpu hdd temp and terminal output"
date: 2009-09-26
forum: General Help
---

### Post by sowhat123456789a on 2009-09-26
```
font Sans:size=8
#xftfont Sans:size=10
use_xft yes
update_interval 1
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 220
maximum_width 220
default_color white
alignment top_left
gap_x 20
gap_y 35
cpu_avg_samples 2
override_utf8_locale no
uppercase yes

TEXT
Uptime: $alignr$uptime

Processes: ${alignr}$processes ($running_processes running)

CPU1 ${alignr}${cpu cpu1}%
${cpubar 4 cpu1}

CPU2 ${alignr}${cpu cpu2}%
${cpubar 4 cpu2}

CPU3 ${alignr}${cpu cpu3}%
${cpubar 4 cpu3}

CPU4 ${alignr}${cpu cpu4}%
${cpubar 4 cpu4}

Ram ${alignr}$mem / $memmax ($memperc%)
${membar 4}

swap ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Highest CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}
${top name 4}$alignr${top cpu 4}${top mem 4}

Highest MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}
${top_mem name 4}$alignr${top_mem cpu 4}${top_mem mem 4}

Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107} ${alignr}${upspeedgraph eth0 25,107}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

HDD WRITE $alignr $diskio_write
${diskiograph_write }
HDD READ $alignr $diskio_read
${diskiograph_read }

```

I have some problems with my conky: First of all, my conkys background is not the same with my destkop. Also I want to show on my conky, infos about hardware like cpus temp, hdd temp, fans rpm (and the others)..... Finally I want to show "lsof -i" output from terminal. But I don't know how to do it :(

Thanks for interest...

---

### Post by karlmp on 2009-09-26
[http://ubuntuforums.org/showthread.php?t=1010741&page=13](http://ubuntuforums.org/showthread.php?t=1010741&page=13)

---

### Post by sowhat123456789a on 2009-09-27
When I add on conky :

CPU FAN${alignr}${exec sensors | grep "fan1:" | cut -c13-16 ;} PRM
HDD$alignr${hddtemp /dev/sda 0.0.0.0 7634}C
MOTHERBOARD $alignr ${hwmon temp 1}C
CPU 1${alignr}${exec sensors | grep "Core 0:" | cut -c13-16 ;}C
CPU 2${alignr}${exec sensors | grep "Core 1:" | cut -c13-16 ;}C
CPU 3${alignr}${exec sensors | grep "Core 2:" | cut -c13-16 ;}C
CPU 4${alignr}${exec sensors | grep "Core 3:" | cut -c13-16 ;}C

it shows me :

cpu fan 2149 rpm
hdd 32 C
motherboard 45 C
cpu1,2,3,4 58-62 C

Are the results true ?

---

### Post by sowhat123456789a on 2009-10-04
last question re-asked... :(

---

