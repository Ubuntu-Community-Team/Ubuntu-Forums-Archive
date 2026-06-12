---
title: "conky error? no network information following new mobo installation"
date: 2010-12-09
forum: General Help
---

### Post by princeofnam on 2010-12-09
I just installed a new mobo and ran Ubuntu again.  Everything works fine but one thing I noticed was that my conky colors setup does't display my network info anymore.

the code is as follows > ${voffset 4}${font Droid Sans:style=Bold:size=8}NETWORK $stippled_hr${font}
# |--WLAN0
${if_up wlan0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed wlan0}${color}${font} ${alignr}${color2}${upspeedgraph wlan0 8,60 51751E 709937}${color}
${goto 32}Total: ${color2}${totalup wlan0}${color}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed wlan0}${color}${font} ${alignr}${color2}${downspeedgraph wlan0 8,60 51751E 709937}${color}
${goto 32}Total: ${color2}${totaldown wlan0}${color}
${voffset -2}${color0}${font Poky:size=14}Y${font}${color}${goto 32} ${voffset -2}Signal: ${font Droid Sans:style=Bold:size=8}${color1}${wireless_link_qual wlan0}%${color}${font} ${alignr}${color2}${wireless_link_bar 8,60 wlan0}${color}
${voffset 4}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -8}Local IP: ${alignr}${color2}${addr wlan0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 ~/.conkycolors/bin/conkyIp}${color}
# |--ETH0
${else}${if_up eth0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed eth0}${color}${font} ${alignr}${color2}${upspeedgraph eth0 8,60 51751E 709937}${color}
${goto 32}Total: ${color2}${totalup eth0}${color}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed eth0}${color}${font} ${alignr}${color2}${downspeedgraph eth0 8,60 51751E 709937}${color}
${goto 32}Total: ${color2}${totaldown eth0}${color}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr eth0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 ~/.conkycolors/bin/conkyIp}${color}
# |--PPP0
${endif}${else}${if_up ppp0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed ppp0}${color}${font} ${alignr}${color2}${upspeedgraph ppp0 8,60 51751E 709937}${color}
${goto 32}Total: ${color2}${totalup ppp0}${color}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed ppp0}${color}${font} ${alignr}${color2}${downspeedgraph ppp0 8,60 51751E 709937}${color}
${goto 32}Total: ${color2}${totaldown ppp0}${color}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr ppp0}${color}
${endif}${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}${goto 32}Network Unavailable${endif}${endif}


Right now it just displays "NETWORK.................................." with nothing after it.

---

### Post by princeofnam on 2010-12-10
anyone? are there any good conky generators besides conky-colors?

---

