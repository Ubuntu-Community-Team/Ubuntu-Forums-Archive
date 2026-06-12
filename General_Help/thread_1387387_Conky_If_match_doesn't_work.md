---
title: "Conky If_match doesn't work"
date: 2010-01-21
forum: General Help
---

### Post by fiddler616 on 2010-01-21
*Note, I'm posting this on behalf of a friend who doesn't understand the magic of these forums.*

Hello,

I have a simple question--I have the following .conkyrc, inspired from [this]("http://crunchbanglinux.org/forums/post/49941/#p49941") post:
[PHP]# conky configuration
#
# The list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.
#
# For ideas about how to modify conky, please see:
# http://crunchbanglinux.org/forums/topic/59/my-conky-config/
#
# For help with conky, please see:
# http://crunchbanglinux.org/forums/topic/2047/conky-help/
#
# Enjoy! :)
##############################################
#  Settings
##############################################
background yes
use_xft yes
xftfont Sans:size=7
xftalpha 1
uppercase no
override_utf8_locale no 

update_interval 2.0
total_run_times 0
cpu_avg_samples 2

own_window yes
own_window_transparent yes
own_window_type desktop
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
maximum_width 250

draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
show_graph_range no
show_graph_scale no
default_color white
default_shade_color black
default_outline_color white

alignment top_right
gap_x 12
gap_y 12
no_buffers yes
##############################################
#  Output
##############################################
TEXT 
$sysname  $kernel  on  $machine
$alignr Uptime: $uptime
${if_match ${battery_percent BAT0} <= 20}${color #aa1111}$endif ${if_match ${battery_percent BAT0} > 20}${color lightgrey}$endif BATT: $battery_percent% $alignr ~${battery_time} 
${battery_bar}$color
DISK:$alignr${fs_used /}/${fs_size /}
SWAP:$alignr$swap/$swapmax
ENTROPY: ($entropy_poolsize) $entropy_bar
${color #ddaa00}RAM:     ${membar}
$alignr$mem/$memmax $color
${cpugraph 45,240 000000 aa2200} ${voffset 20}${goto 30}CPU: ${cpu cpu0}%   ${acpitemp}C${voffset -20}
${hr}
${color}Name                         ${goto 110} PID#           ${goto 160}CPU%            ${goto 210}MEM${font sans:size=7}
${color   #ddaa00}  ${top     name 1}${goto 110}${top     pid 1}${goto 160}${top     cpu 1}${goto 210}${top     mem 1}
${color lightgrey}  ${top     name 2}${goto 110}${top     pid 2}${goto 160}${top     cpu 2}${goto 210}${top     mem 2}
${color lightgrey}  ${top     name 3}${goto 110}${top     pid 3}${goto 160}${top     cpu 3}${goto 210}${top     mem 3}
${color lightgrey}  ${top     name 4}${goto 110}${top     pid 4}${goto 160}${top     cpu 4}${goto 210}${top     mem 3}
${color   #ddaa00}  ${top_mem name 1}${goto 110}${top_mem pid 1}${goto 160}${top_mem cpu 1}${goto 210}${top_mem mem 1}
${color lightgrey}  ${top_mem name 2}${goto 110}${top_mem pid 2}${goto 160}${top_mem cpu 2}${goto 210}${top_mem mem 2}
${color lightgrey}  ${top_mem name 3}${goto 110}${top_mem pid 3}${goto 160}${top_mem cpu 3}${goto 210}${top_mem mem 3}
${color lightgrey}  ${top_mem name 4}${goto 110}${top_mem pid 4}${goto 160}${top_mem cpu 4}${goto 210}${top_mem mem 3}
$font ${hr}
${color #f08000}${font sans:size=10}Wireless:$font$color   (eth1 ${addrs eth1})
${downspeedgraph eth1 45,240 000000 ff8800} ${goto 30}Down: ${goto 30}${voffset 14}${downspeed eth1}k/s [${totaldown eth1}]${voffset -14}
${upspeedgraph   eth1 45,240 000000 ff8800} ${goto 30}Up:   ${goto 30}${voffset 14}${upspeed   eth1}k/s [${totalup   eth1}]${voffset -14}
${hr}
${color #995533}${font sans:size=10}Hotkeys: $font$color
  Super+_${tab  40}Main Menu
  Super+\t${tab 40}Client Menu
  Super+r${tab  40}Run Dialog
  Super+t${tab  40}Terminal
  Super+f${tab  40}File Manager
  Super+e${tab  40}Editor
  Super+m${tab  40}Media Player
  Super+w${tab  40}Web Browser
  Super+g${tab  40}Graphics Editor
  Super+l${tab  40}Lock Screen
  Super+u${tab  40}System Update
  Super+v${tab  40}Volume
  Super+x${tab  40}Logout
[/PHP]

and it produces this:

[IMG]http://imgur.com/Q3Qt7.png[/IMG]
As you can see, the 
```

${if_match ${battery_percent BAT0} <= 20}${color #aa1111}$endif ${if_match ${battery_percent BAT0} > 20}${color lightgrey}$endif 
```
lines aren't working right, and I'm absolutely baffled as to why. How do I fix it?

Thanks in advance.

---

### Post by stinkeye on 2010-01-21
Try using quotation marks
```
${if_match "${battery_percent BAT0}" <= "20"}${color #aa1111}$endif ${if_match "${battery_percent BAT0}" > "20"}${color lightgrey}$endif
```

or maybe they're using an old version of conky that doesn't support if_match.

---

