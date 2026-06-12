---
title: "Conky graphs not working"
date: 2010-08-22
forum: General Help
---

### Post by tmandpea on 2010-08-22
Hey everyone. So I have conky up and running, but today as I was messing around with the colors for the custom theme, the graphs for cpu temp and network up and down aren't displaying anything. Any ideas what's going on?

Here's my conky configuration:

./conky-colors --lang=english --theme=custom --color0=000000 --color1=800080 --color2=800080 --cpu=2 --cputemp --swap --updates --hdtemp1=sda --proc=3 --calendar --m --network --rhythmbox=oldvinyl --ubuntu --alllight --unit=F --clock=off

---

### Post by Quackers on 2010-08-22
Post your .conkyrc and any template you are using by using the CODE tags (click on # in New Reply)

---

### Post by tmandpea on 2010-08-22
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
own_window_class Conky
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

default_color 212526

color0 000000
color1 800080
color2 800080

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
${offset 1}${color0}${font Poky:size=16}P${font}${offset -19}${voffset 9}${cpubar cpu0 4,18}${color}${voffset -16}${goto 32}CPU1: ${font Droid Sans:style=Bold:size=8}${color1}${cpu cpu1}%${font} ${alignr}${font Droid Sans:style=Bold:size=8}${color1}${execi 30 sensors -f | grep 'Core 0' | cut -c14-16}°F${color}${font}  ${color2}${cpugraph cpu1 8,50 800080}${color}
${goto 32}CPU2: ${font Droid Sans:style=Bold:size=8}${color1}${cpu cpu2}%${font} ${alignr}${font Droid Sans:style=Bold:size=8}${color1}${execi 30 sensors -f | grep 'Core 1' | cut -c14-16}°F${color}${font}  ${color2}${cpugraph cpu2 8,50 800080}${color}
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
#############
# - CLOCK - #
#############
${voffset 4}${font Droid Sans:style=Bold:size=8}DATE $stippled_hr${font}
${alignc}${time %d %B %Y}
################
# - CALENDAR - #
################
${voffset -2}${color0}${font Poky:size=15}d${font}${color}${voffset -8}${font Liberation Mono:size=8}${execpi 10800 DJS=`date +%-d`; cal | sed 's/^/${goto 32} /' | sed '1d' | sed s/" $DJS "/" "'${font Liberation Mono:style=bold:size=8}${color1}'"$DJS"'${color}${font}${font Liberation Mono:size=8}'" "/}${font}${font}${voffset -14}
#################
# - RHYTHMBOX - #
#################
${voffset 4}${font Droid Sans:style=Bold:size=8}RHYTHMBOX $stippled_hr${font}
${execi 10 ~/.conkycolors/bin/conkyCover}${execpi 10 ~/.conkycolors/bin/conkyRhythmbox -t ~/.conkycolors/templates/conkyPlayer.template}
###############
# - NETWORK - #
###############
${voffset 4}${font Droid Sans:style=Bold:size=8}NETWORK $stippled_hr${font}
# |--WLAN0
${if_up wlan0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed wlan0}${color}${font} ${alignr}${color2}${upspeedgraph wlan0 8,60 800080}${color}
${goto 32}Total: ${color2}${totalup wlan0}${color}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed wlan0}${color}${font} ${alignr}${color2}${downspeedgraph wlan0 8,60 800080}${color}
${goto 32}Total: ${color2}${totaldown wlan0}${color}
${voffset -2}${color0}${font Poky:size=14}Y${font}${color}${goto 32} ${voffset -2}Signal: ${font Droid Sans:style=Bold:size=8}${color1}${wireless_link_qual wlan0}%${color}${font} ${alignr}${color2}${wireless_link_bar 8,60 wlan0}${color}
${voffset 4}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -8}Local IP: ${alignr}${color2}${addr wlan0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 ~/.conkycolors/bin/conkyIp}${color}
# |--ETH0
${else}${if_up eth0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed eth0}${color}${font} ${alignr}${color2}${upspeedgraph eth0 8,60 800080}${color}
${goto 32}Total: ${color2}${totalup eth0}${color}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed eth0}${color}${font} ${alignr}${color2}${downspeedgraph eth0 8,60 800080}${color}
${goto 32}Total: ${color2}${totaldown eth0}${color}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr eth0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 ~/.conkycolors/bin/conkyIp}${color}
# |--PPP0
${endif}${else}${if_up ppp0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed ppp0}${color}${font} ${alignr}${color2}${upspeedgraph ppp0 8,60 800080}${color}
${goto 32}Total: ${color2}${totalup ppp0}${color}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed ppp0}${color}${font} ${alignr}${color2}${downspeedgraph ppp0 8,60 800080}${color}
${goto 32}Total: ${color2}${totaldown ppp0}${color}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr ppp0}${color}
${endif}${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}${goto 32}Network Unavailable${endif}${endif}
```

---

### Post by Quackers on 2010-08-22
Yours is completely different to my setup. I don't know where to begin to look, because it is so different.
Here is the relevant section from my .conkyrc

```
${font Terminus:style=bold:size=11}PROCESSORS $hr
CPU1: ${cpu cpu1}% ${cpubar cpu1}
CPU2: ${cpu cpu2}% ${cpubar cpu2}
```

I'm not saying yours is wrong and mine is right. I'm just saying they are completely different :confused:
Sorry I can't help any more.

---

### Post by tmandpea on 2010-08-22
Thats alright:p

---

