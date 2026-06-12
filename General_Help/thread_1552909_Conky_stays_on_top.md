---
title: "Conky stays on top"
date: 2010-08-14
forum: General Help
---

### Post by Sonybuntu on 2010-08-14
I've tried other solutions, but none work for me.

Here is my .conkyrc
```
######################
# - Conky settings - #
######################
update_interval 1
total_run_times 0
net_avg_samples 1
cpu_avg_samples 1

imlib_cache_size 0
double_buffer yes
no_buffers yes

#####################
# - Text settings - #
#####################
use_xft yes
xftfont Droid Sans:size=8
override_utf8_locale yes
text_buffer_size 2048

#############################
# - Window specifications - #
#############################
on_bottom yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

alignment top_right
gap_x 25
gap_y 40
minimum_size 182 0
maximum_width 182

default_bar_size 60 8

#########################
# - Graphics settings - #
#########################
draw_shades no

default_color D6D6D6

color0 FFFFFF
color1 7296BB
color2 FFFFFF

TEXT
${font Droid Sans:style=Bold:size=8}SYSTEM $stippled_hr${font}
##############
# - SYSTEM - #
##############
${color0}${voffset 6}${font OpenLogos:size=19}u${font}${color}${goto 32}${voffset -14}Kernel:  ${alignr}${color2}${kernel}${color}
${goto 32}Uptime: ${alignr}${color2}${uptime}${color}
# |--UPDATES
${goto 32}Updates: ${alignr}${font Droid Sans:style=Bold:size=8}${color1}${execi 360 aptitude search "~U" | wc -l | tail}${color}${font} ${color2}Packages${color}
# |--CPU
${offset 1}${color0}${font Poky:size=16}P${font}${offset -19}${voffset 9}${cpubar cpu0 4,18}${color}${voffset -16}${goto 32}CPU1: ${font Droid Sans:style=Bold:size=8}${color1}${cpu cpu1}%${font} ${alignr}${font Droid Sans:style=Bold:size=8}${color1}${execi 30 sensors -f | grep 'Core 0' | cut -c14-16}°F${color}${font}  ${color2}${cpugraph cpu1 8,50 7296BB 7296BB}${color}
${goto 32}CPU2: ${font Droid Sans:style=Bold:size=8}${color1}${cpu cpu2}%${font} ${alignr}${font Droid Sans:style=Bold:size=8}${color1}${execi 30 sensors -f | grep 'Core 1' | cut -c14-16}°F${color}${font}  ${color2}${cpugraph cpu2 8,50 7296BB 7296BB}${color}
# |--MEM
${color0}${font Poky:size=16}M${font}${color}${goto 32}${voffset -7}RAM: ${font Droid Sans:style=Bold:size=8}${color1}$memperc%${color}${font}
${offset 1}${voffset 2}${color0}${membar 4,18}${color}${goto 32}${voffset -2}F: ${color2}${memeasyfree}${color} U: ${color2}${mem}${color}
# |--CPU
${voffset 2}${color0}${font Poky:size=14}s${font}${color}${voffset -8}${goto 32}SWAP: ${font Droid Sans:style=Bold:size=8}${color1}${swapperc}%${color}${font}
${voffset 4}${offset 1}${color2}${swapbar 4,18}${color}${voffset -4}${goto 32}F: ${color2}$swapmax${color} U: ${color2}$swap${color}
# |--PROC
${voffset 2}${color0}${font Poky:size=15}a${font}${color}${goto 32}${voffset -10}Processes: ${color2}${alignr 13}CPU${alignr}RAM${color}
${voffset -1}${goto 42}${color2}${top name 1}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 1}${alignr }${top mem 1}${color}${font}
${voffset -1}${goto 42}${color2}${top name 2}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 2}${alignr }${top mem 2}${color}${font}
${voffset -1}${goto 42}${color2}${top name 3}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 3}${alignr }${top mem 3}${color}${font}
${voffset -1}${goto 42}${color2}${top name 4}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 4}${alignr }${top mem 4}${color}${font}
${voffset -1}${goto 42}${color2}${top name 5}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 5}${alignr }${top mem 5}${color}${font}
#############
# - CLOCK - #
#############
${voffset 4}${font Droid Sans:style=Bold:size=8}DATE $stippled_hr${font}
${voffset -12}${goto 28}${font Arial Black:size=38}${color2}${time %H}${color}${font}${voffset -28}${font Droid Sans:style=Bold:size=11}${color2}${time :%M}${time :%S}${color}${font}
${voffset -2}${goto 100}${font Droid Sans:style=Bold:size=8}${color2}${time %A}${color}${font}
${goto 100}${time %d %b %Y}
################
# - CALENDAR - #
################
${voffset -2}${color0}${font Poky:size=15}d${font}${color}${voffset -8}${font Liberation Mono:size=8}${execpi 10800 DJS=`date +%-d`; cal | sed 's/^/${goto 32} /' | sed '1d' | sed s/" $DJS "/" "'${font Liberation Mono:style=bold:size=8}${color1}'"$DJS"'${color}${font}${font Liberation Mono:size=8}'" "/}${font}${font}${voffset -14}
##########
# - HD - #
##########
${voffset 4}${font Droid Sans:style=Bold:size=8}HD $stippled_hr${font}
# |--HDTEMP1
  ${voffset 4}${color0}${font Weather:size=15}y${font}${color}${voffset -3}${goto 32}Temperature: ${font Droid Sans:style=Bold:size=8}${color1}${execi 120 hddtemp /dev/sda -n --unit=F}°F${color}${font}${alignr}${color2}/dev/sda${color}
${execpi 30 ~/.conkycolors/bin/conkyHD1}
###############
# - NETWORK - #
###############
${voffset 4}${font Droid Sans:style=Bold:size=8}NETWORK $stippled_hr${font}
# |--WLAN0
${if_up wlan0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed wlan0}${color}${font} ${alignr}${color2}${upspeedgraph wlan0 8,60 7296BB 7296BB}${color}
${goto 32}Total: ${color2}${totalup wlan0}${color}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed wlan0}${color}${font} ${alignr}${color2}${downspeedgraph wlan0 8,60 7296BB 7296BB}${color}
${goto 32}Total: ${color2}${totaldown wlan0}${color}
${voffset -2}${color0}${font Poky:size=14}Y${font}${color}${goto 32} ${voffset -2}Signal: ${font Droid Sans:style=Bold:size=8}${color1}${wireless_link_qual wlan0}%${color}${font} ${alignr}${color2}${wireless_link_bar 8,60 wlan0}${color}
${voffset 4}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -8}Local IP: ${alignr}${color2}${addr wlan0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 ~/.conkycolors/bin/conkyIp}${color}
# |--ETH0
${else}${if_up eth0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed eth0}${color}${font} ${alignr}${color2}${upspeedgraph eth0 8,60 7296BB 7296BB}${color}
${goto 32}Total: ${color2}${totalup eth0}${color}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed eth0}${color}${font} ${alignr}${color2}${downspeedgraph eth0 8,60 7296BB 7296BB}${color}
${goto 32}Total: ${color2}${totaldown eth0}${color}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr eth0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 ~/.conkycolors/bin/conkyIp}${color}
# |--PPP0
${endif}${else}${if_up ppp0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed ppp0}${color}${font} ${alignr}${color2}${upspeedgraph ppp0 8,60 7296BB 7296BB}${color}
${goto 32}Total: ${color2}${totalup ppp0}${color}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed ppp0}${color}${font} ${alignr}${color2}${downspeedgraph ppp0 8,60 7296BB 7296BB}${color}
${goto 32}Total: ${color2}${totaldown ppp0}${color}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr ppp0}${color}
${endif}${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}${goto 32}Network Unavailable${endif}${endif}
###############
# - WEATHER - #
###############
# For a working weather script you NEED to define, in a user specific config file, a partner id and registration code for the weather.com xoap service. For this purpose copy .conkyForecast.config in ~/.conkycolors folder to your home and setup as required.
# http://www.weather.com/services/xmloap.html
${voffset -8}${font Droid Sans:style=Bold:size=8}WEATHER $stippled_hr${font}
# |--WLAN0
${if_up wlan0}
${execpi 10800 ~/.conkycolors/bin/conkyForecast --location=23602 -i -t ~/.conkycolors/templates/conkyForecast.template}
# |--ETH0
${else}${if_up eth0}
${execpi 10800 ~/.conkycolors/bin/conkyForecast --location=23602 -i -t ~/.conkycolors/templates/conkyForecast.template}
# |--PPP0
${endif}${else}${if_up ppp0}
${execpi 10800 ~/.conkycolors/bin/conkyForecast --location=23602 -i -t ~/.conkycolors/templates/conkyForecast.template}
${endif}${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}${goto 32}Weather Unavailable${endif}${endif}
```

I'm using Conky-Colors and Conky is 1.8.

Terminal output when entering Conky:
```
Conky: /home/jonathan/.conkyrc: 24: no such configuration: 'on_bottom'
Conky: desktop window (a8) is root window
Conky: window type - override
Conky: drawing to created window (0x5a00001)
Conky: drawing to double buffer
```

---

### Post by elliotn on 2010-08-14
Change the line

window type-override 


To
window type-normal

---

### Post by Sonybuntu on 2010-08-14
> **elliotn said:**
> Change the line

window type-override 


To
window type-normal

This seems to work so far, but I'm not marking it as solved yet. Other solutions seemed to work, but 5 min. later, poof! Conky floats to the top.

Okay! It works!

---

### Post by xircon on 2010-09-02
Thank you!!  Conky started playing up last night and I was on the verge of abandoning it.  It had been running fine for weeks, cannot work out what had changed, but this fixed it.

---

