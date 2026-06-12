---
title: "Yet Another Conky Thread"
date: 2009-08-12
forum: General Help
---

### Post by theredcross on 2009-08-12
I am experimenting with conky again after testing out kde 4 for the first time (4.3 to be exact), and I have a strange problem. The own_window and own_window_hints commands seem to work fine, and it is anchored against the desktop, but the background is solid black instead of transparent. ```
use_xft yes
xftfont verdana:size=8
alignment bottom_right
xftalpha 0.8
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58



TEXT
${color BADCDD}${font weather:size=82}${execi 600 ~/scripts/conditions.sh}${color}${font}${voffset -25}  ${execi 1200 ~/scripts/pogodynka.sh}

   ${font weather:size=28}x ${font}HDD ${execi 1 ~/scripts/hddmonit.sh}&#65533;C 
    
   ${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth0} Kb/s 
   ${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth0} Kb/s 

   ${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth0}
   ${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth1}0

   ${color ffffff}${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
   ${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}


   ${color F8DF58}${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py theredcrosss c0mmand 3}

   ${color C2E078}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax


 ${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %H:%M}


```
I am also running compiz and emerald, but I didn't see any difference when I ran kwin.

---

### Post by akshunj on 2009-08-16
Same issue.  And there are no good simple system monitors that actually work with KDE 4.3 anymore.  Why is it so tough to get something basic like conky running properly???

---

