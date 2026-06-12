---
title: "Yet Another Conky Question"
date: 2010-10-31
forum: General Help
---

### Post by SOG420 on 2010-10-31
I'm just discovering the awesomeness of Conky but I'm having a few issues with some add ons for conkyForecast and Audacious
here is my conkyrc file 


use_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 250
maximum_width 260
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color black
default_outline_color white
alignment bottom_left
gap_x 10
gap_y 10
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale no
use_spacer yes
draw_bar_border yes
color0 A4D3EE # first block
color1 CD0000 #secondblock
color2 A4D3EE #third block
color3 ffffcc #fourth block
color4 white #ubuntu logo

TEXT

${voffset 5}$color0${font Starcraft::pixelsize=25}Jeffrey${font OpenLogos::pixelsize=30}${color orange}$alignr u
$color0${font Junkyard:bold:size=9}${voffset -13}/%BrAiN%\  ${voffset -3}$hr 2${font Zekton:size=8}
Time:      $alignr${time %H:%Mh}
Date:       $alignr${time %d %b. %Y %A}
Kernel:    $alignr$kernel
Uptime:    $alignr$uptime
Cpu Temp:  $alignr${acpitemp}F
Cpu Freq:  $alignr${freq}mhz
$color1${font Junkyard:bold:size=9}RAM  ${voffset -3}$hr 2 ${font Zekton:size=8}
cpu speed:
${cpubar 4}
ram graph:
${cpugraph 000000 cc99cc}
$hr
Highest CPU $alignr CPU%  MEM%
${top name 1}$alignr${top cpu 1}   ${top mem 1}
${top name 2}$alignr${top cpu 2}   ${top mem 2}
${top name 3}$alignr${top cpu 3}   ${top mem 3}
$hr
Highest MEM $alignr CPU%  MEM%
${top_mem name 1}$alignr${top_mem cpu 1}  ${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}   ${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}   ${top_mem mem 3}
$color1${font Junkyard:bold:size=9}Brain Log  ${voffset -3}$hr 2 ${font Zekton:size=8}
RAM:  $memperc% ${membar 4}
Swap: $swapperc% ${swapbar 4}
$color2${font Junkyard:bold:size=9}Hard Drive Space  ${voffset -3}$hr 2${font Zekton:size=8}
/Root:
${fs_used_perc /}% ${fs_bar 4 /}
#/DL:
#${fs_used_perc /~/Downloads}% ${fs_bar 4 /~/Downloads}
/Winback:
${fs_used_perc /media/Winback}% ${fs_bar 4 /media/Winback}
Hard Drive Info I/O
${diskiograph 20,250 000000 0000ff }
${color #0077ff}HD IO: ${color orange}${diskio} 
${color #0077ff}${diskiograph 000000 0077ff}
$hr
$color3${font Junkyard:bold:size=9}Outside World  ${voffset -3}$hr 2${font Zekton:size=8}
Down: ${color 99ff99}${downspeed wlan0} k/s ${alignr}$color3 Up: ${color ff3333}${upspeed wlan0} k/s $color3
${downspeedgraph wlan0 20,130 000000 99ff99} ${alignr}${upspeedgraph wlan0 20,130 000000 ff3333}
Wireless Link Quality:
${wireless_link_qual_perc wlan0}% ${wireless_link_bar 4 wlan0}
Conditions: ${execi 3600 conkyForecast --location=USKY1108 --datatype=CC}
${font ConkyWeather:size=36}${execi 3600 conkyForecast --location=USKY108 --datatype=WF}${font}
Temp: ${execi 3600 conkyForecast --location=USKY1108 --datatype=HT}
<br>
here's what the terminal spits out

/usr/bin/conkyForecast: 3: /usr/bin/python2: not found
/usr/bin/conkyForecast: 3: /usr/bin/python2: not found
/usr/bin/conkyForecast: 3: /usr/bin/python2: not found

---

### Post by JOHNNYG713 on 2010-10-31
try this to fix weather.
solution:

open terminal 

sudo gedit /usr/bin/conkyForecast

"/usr/bin/python2 /usr/share/conkyforecast/conkyForecast.py"

change it to

"/usr/bin/python /usr/share/conkyforecast/conkyForecast.py"

and it will work again  [IMG]http://forumubuntusoftware.info/images/smilies/icon_razz.gif[/IMG]

---

### Post by Vigh on 2010-10-31
is conky ubuntu weather forecasts? would be really useful to have, i was thinking of writing a meteorology app that connects to the official meterology info for Australia for Ubuntu/Linux, not sure how to do this but at this stage

---

