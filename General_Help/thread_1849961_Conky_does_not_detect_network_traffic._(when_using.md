---
title: "Conky does not detect network traffic. (when using wifi)"
date: 2011-09-25
forum: General Help
---

### Post by Crypz on 2011-09-25
[IMG]http://www.upload.ee/image/1686974/Untitled.jpg[/IMG]


Right before posting i realized it works perfectly with wired connection but does not work with wifi.

What needs to be changed?


my conky network config:

```
###############
# - NETWORK - #
###############
${voffset 4}${font Ubuntu:style=Bold:size=8}NETWORK $stippled_hr${font}
# |--WLAN0
${if_up wlan0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Ubuntu:style=Bold:size=8}${color1}${upspeed wlan0}${color}${font} ${alignr}${color2}${upspeedgraph wlan0 8,60 A40000 C22F2F}${color}
${goto 32}Total: ${font Ubuntu:style=Bold:size=8}${color2}${totalup wlan0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Ubuntu:style=Bold:size=8}${color1}${downspeed wlan0}${color}${font} ${alignr}${color2}${downspeedgraph wlan0 8,60 A40000 C22F2F}${color}
${goto 32}Total: ${font Ubuntu:style=Bold:size=8}${color2}${totaldown wlan0}${color}${font}
${voffset -2}${color0}${font Poky:size=14}Y${font}${color}${goto 32}${voffset -2}Signal: ${font Ubuntu:style=Bold:size=8}${color1}${wireless_link_qual_perc wlan0}%${color}${font} ${alignr}${color2}${wireless_link_bar 8,60 wlan0}${color}
${voffset 4}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -8}Local IP: ${alignr}${color2}${addr wlan0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 /usr/share/conkycolors/bin/conkyIp}${color}
# |--ETH0
${else}${if_up eth0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Ubuntu:style=Bold:size=8}${color1}${upspeed eth0}${color}${font} ${alignr}${color2}${upspeedgraph eth0 8,60 A40000 C22F2F}${color}
${goto 32}Total: ${font Ubuntu:style=Bold:size=8}${color2}${totalup eth0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Ubuntu:style=Bold:size=8}${color1}${downspeed eth0}${color}${font} ${alignr}${color2}${downspeedgraph eth0 8,60 A40000 C22F2F}${color}
${goto 32}Total: ${font Ubuntu:style=Bold:size=8}${color2}${totaldown eth0}${color}${font}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr eth0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 /usr/share/conkycolors/bin/conkyIp}${color}
# |--PPP0
${else}${if_up ppp0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Ubuntu:style=Bold:size=8}${color1}${upspeed ppp0}${color}${font} ${alignr}${color2}${upspeedgraph ppp0 8,60 A40000 C22F2F}${color}
${goto 32}Total: ${font Ubuntu:style=Bold:size=8}${color2}${totalup ppp0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Ubuntu:style=Bold:size=8}${color1}${downspeed ppp0}${color}${font} ${alignr}${color2}${downspeedgraph ppp0 8,60 A40000 C22F2F}${color}
${goto 32}Total: ${font Ubuntu:style=Bold:size=8}${color2}${totaldown ppp0}${color}${font}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr ppp0}${color}
${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}${goto 32}Network Unavailable${voffset 14}${endif}${endif}${endif}
```

EDIT: config had wrong connection interface, changed it to eth1

---

