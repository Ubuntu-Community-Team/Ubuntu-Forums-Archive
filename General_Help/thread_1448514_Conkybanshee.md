---
title: "Conky/banshee"
date: 2010-04-06
forum: General Help
---

### Post by dr.pepper23 on 2010-04-06
I'm using a banshee widget with conky. All the information in conky updates every second, except for the banshee part which only updates every 10 seconds or so. Anybody know why this is?
Here is my conkyrc:

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
xftfont Liberation Sans:size=8
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

default_color cccccc

color0 white
color1 C22F2F
color2 white

TEXT
${font Liberation Sans:style=Bold:size=8}SYSTEM $stippled_hr${font}
##############
# - SYSTEM - #
##############
${color0}${voffset 6}${font OpenLogos:size=19}u${font}${color}${goto 32}${voffset -14}Kernel:  ${alignr}${color2}${kernel}${color}
${goto 32}Uptime: ${alignr}${color2}${uptime}${color}
# |--UPDATES
${goto 32}Updates: ${alignr}${font Liberation Sans:style=Bold:size=8}${color1}${execi 360 aptitude search "~U" | wc -l | tail}${color}${font} ${color2}Packages${color}
# |--CPU
${offset 1}${color0}${font Poky:size=16}P${font}${offset -19}${voffset 9}${cpubar cpu0 4,18}${color}${voffset -16}${goto 32}CPU1: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu1}%${color}${font} ${alignr}${color2}${cpugraph cpu1 8,60 A40000 C22F2F}${color}
${goto 32}CPU2: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu2}%${color}${font} ${alignr}${color2}${cpugraph cpu2 8,60 A40000 C22F2F}${color}
# |--MEM
${color0}${font Poky:size=16}M${font}${color}${goto 32}${voffset -7}RAM: ${font Liberation Sans:style=Bold:size=8}${color1}$memperc%${color}${font}
${offset 1}${voffset 2}${color0}${membar 4,18}${color}${goto 32}${voffset -2}F: ${color2}${memeasyfree}${color} U: ${color2}${mem}${color}
# |--PROC
${voffset 2}${color0}${font Poky:size=15}a${font}${color}${goto 32}${voffset -10}Processes: ${color2}${alignr 13}CPU${alignr}RAM${color}
${voffset -1}${goto 42}${color2}${top name 1}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 1}${alignr }${top mem 1}${color}${font}
${voffset -1}${goto 42}${color2}${top name 2}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 2}${alignr }${top mem 2}${color}${font}
${voffset -1}${goto 42}${color2}${top name 3}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 3}${alignr }${top mem 3}${color}${font}
${voffset -1}${goto 42}${color2}${top name 4}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 4}${alignr }${top mem 4}${color}${font}
${voffset -1}${goto 42}${color2}${top name 5}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 5}${alignr }${top mem 5}${color}${font}
#############
# - CLOCK - #
#############
${voffset 4}${font Liberation Sans:style=Bold:size=8}DATE $stippled_hr${font}
${voffset -12}${goto 28}${font Arial Black:size=38}${color2}${time %H}${color}${font}${voffset -28}${font Liberation Sans:style=Bold:size=11}${color2}${time :%M}${time :%S}${color}${font}
${voffset -2}${goto 100}${font Liberation Sans:style=Bold:size=8}${color2}${time %A}${color}${font}
${goto 100}${time %d %b %Y}
###############
# - BANSHEE - #
###############
${voffset 4}${font Liberation Sans:style=Bold:size=8}BANSHEE $stippled_hr${font}
${execi 10 ~/.conkycolors/bin/conkyCover}${execpi 10 ~/.conkycolors/bin/conkyBanshee -t ~/.conkycolors/templates/conkyPlayer.template}
###############
# - NETWORK - #
###############
${voffset 4}${font Liberation Sans:style=Bold:size=8}NETWORK $stippled_hr${font}
# |--WLAN0
${if_up wlan0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Liberation Sans:style=Bold:size=8}${color1}${upspeed wlan0}${color}${font} ${alignr}${color2}${upspeedgraph wlan0 8,60 A40000 C22F2F}${color}
${goto 32}Total: ${color2}${totalup wlan0}${color}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Liberation Sans:style=Bold:size=8}${color1}${downspeed wlan0}${color}${font} ${alignr}${color2}${downspeedgraph wlan0 8,60 A40000 C22F2F}${color}
${goto 32}Total: ${color2}${totaldown wlan0}${color}
${voffset -2}${color0}${font Poky:size=14}Y${font}${color}${goto 32} ${voffset -2}Signal: ${font Liberation Sans:style=Bold:size=8}${color1}${wireless_link_qual wlan0}%${color}${font} ${alignr}${color2}${wireless_link_bar 8,60 wlan0}${color}
${voffset 4}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -8}Local IP: ${alignr}${color2}${addr wlan0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 ~/.conkycolors/bin/conkyIp}${color}
# |--ETH0
${else}${if_up eth0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Liberation Sans:style=Bold:size=8}${color1}${upspeed eth0}${color}${font} ${alignr}${color2}${upspeedgraph eth0 8,60 A40000 C22F2F}${color}
${goto 32}Total: ${color2}${totalup eth0}${color}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Liberation Sans:style=Bold:size=8}${color1}${downspeed eth0}${color}${font} ${alignr}${color2}${downspeedgraph eth0 8,60 A40000 C22F2F}${color}
${goto 32}Total: ${color2}${totaldown eth0}${color}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr eth0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 ~/.conkycolors/bin/conkyIp}${color}
# |--PPP0
${endif}${else}${if_up ppp0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Liberation Sans:style=Bold:size=8}${color1}${upspeed ppp0}${color}${font} ${alignr}${color2}${upspeedgraph ppp0 8,60 A40000 C22F2F}${color}
${goto 32}Total: ${color2}${totalup ppp0}${color}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Liberation Sans:style=Bold:size=8}${color1}${downspeed ppp0}${color}${font} ${alignr}${color2}${downspeedgraph ppp0 8,60 A40000 C22F2F}${color}
${goto 32}Total: ${color2}${totaldown ppp0}${color}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr ppp0}${color}
${endif}${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}${goto 32}Network Unavailable${endif}${endif}
###############
# - WEATHER - #
###############
# For a working weather script you NEED to define, in a user specific config file, a partner id and registration code for the weather.com xoap service. For this purpose copy .conkyForecast.config in ~/.conkycolors folder to your home and setup as required.
# http://www.weather.com/services/xmloap.html
${voffset -8}${font Liberation Sans:style=Bold:size=8}WEATHER $stippled_hr${font}
# |--WLAN0
${if_up wlan0}
${execpi 10800 ~/.conkycolors/bin/conkyForecast --location=USNC0768 -i -t ~/.conkycolors/templates/conkyForecast.template}
# |--ETH0
${else}${if_up eth0}
${execpi 10800 ~/.conkycolors/bin/conkyForecast --location=USNC0768 -i -t ~/.conkycolors/templates/conkyForecast.template}
# |--PPP0
${endif}${else}${if_up ppp0}
${execpi 10800 ~/.conkycolors/bin/conkyForecast --location=USNC0768 -i -t ~/.conkycolors/templates/conkyForecast.template}
${endif}${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}${goto 32}Weather Unavailable${endif}${endif}
```

---

### Post by dr.pepper23 on 2010-04-06
Nevermind I figured it out. Had to change execi and execpi to 1.

---

