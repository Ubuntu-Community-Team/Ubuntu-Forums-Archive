---
title: "help with conky weather"
date: 2010-04-23
forum: General Help
---

### Post by dluzius on 2010-04-23
My conky works great, except for the part about showing weather. I'm easing
into it, by asking it,at first, to only show moon phases. I've installed the font moon phases for systemwide use. Here's my .conkyrc file, can someone please help me, I am completely lost, and hopelessly confused.

background		no
use_xft			yes
xftfont			Courier:size=16
double_buffer		yes
update_interval		1
alignment		tr
gap_x			60
gap_y			10
no_buffers		yes
minimum_size 		465x500
pad_percents		3
draw_shades no
temperature_unit         fahrenheit
TEXT


${font :size=18 Bold}${color orange}$nodename - $sysname $kernel
$alignc IP ADDRESS  ${addr}
$alignc Karmic  Koala
${hr 1}
# _short added to following line to ignore minutes and seconds
${color yellow}Uptime: $uptime_short

${color #00FF00}RAM: $memperc% ${membar 10}
${color #FF0000}CPU: $cpu% ${cpubar 10}

${color green}Procs: $processes       Run:$running_processes 
${color YELLOW}HDD USAGE ${hr 1}
       ${fs_used /}/${fs_size /}${alignr}${fs_used_perc /}%
${fs_bar 20 /}
${color #00FF00}Down: ${downspeedf eth0}k/s ${alignr}${totaldown eth0} total
${downspeedgraph eth0}
${color #00FF00}Up: ${upspeedf eth0}k/s ${alignr}${totalup eth0} total
${upspeedgraph eth0}
${color orange}$alignc${font :size=18}${time %A, %d %B}    ${time %H:%Mh:%S} 
#WEATHER ${hr 2}
 
${voffset 0}${color #FFFFFF}Moon Phase: ${alignc}${execi 600 conkyForecast --location=USMI0060 --${font Moon Phases :size=40}${color #FFFFF0} --datatype=MP}


thank you, dave

---

