---
title: "Conky how do I end if?"
date: 2010-06-02
forum: General Help
---

### Post by inso_741 on 2010-06-02
this is the part I'm stuck at
```
NETWORK INFO ${voffset -2}${hr 2}
${if_up eth0}${voffset 5}Dynamic IP ${alignr}${execi 3600 wget -O - http://whatismyip.org/ | tail}
Local IP $alignr${addr eth0}
Upload (${totalup eth0})$alignr${upspeedf eth0} kB/s
Download (${totaldown eth0})$alignr${downspeedf eth0} kB/s
$hr
${else}${voffset 5}No network found!

test
```
now how do I end the if_up at the line "No network found!" so that the word 'test' is displayed
I've tried adding $endif after that line but it doesn't work...:(

---

### Post by j.scott.gwin on 2010-06-02
I'm sorry that I don't know, but I thought I'd give you my network code.  It doesn't do exactly what you're trying to do, but here it is anyway.  Also, if you haven't been to [http://conky.linux-hardcore.com/](http://conky.linux-hardcore.com/) give them a try.  You might find your answer there plus there is some truly sick conkys there.

${font Vibrocentric:size=16}${color white}WIRED${font} ${hr 2}
${color yellow}${font Pie charts for maps:size=10}   Local IP: ${alignr}${addr eth0}
${color yellow}${font Pie charts for maps:size=10}   Up: ${upspeed eth0} ${alignr}${upspeedgraph wlan0 10,100 000000 000000}
${color yellow}${font Pie charts for maps:size=10}   Down: ${downspeed eth0} ${alignr}${downspeedgraph wlan0 10,100 000000 000000}
${color yellow}${font Pie charts for maps:size=10}   Upload Total: ${alignr}${totalup eth0}
${color yellow}${font Pie charts for maps:size=10}   Download Total: ${alignr}${totaldown eth0}
${font Vibrocentric:size=16}${color white}WIRELESS${font} ${hr 2}
${font Vibrocentric:size=16}${color red} $alignc Signal: ${wireless_link_qual wlan0}%
${color yellow}${font Pie charts for maps:size=10}   Local IP: ${alignr}${addr wlan0}
${color yellow}${font Pie charts for maps:size=10}   essid: ${alignr}${wireless_essid wlan0}
${color yellow}${font Pie charts for maps:size=10}   Mode: ${alignr}${wireless_mode wlan0}
${color yellow}${font Pie charts for maps:size=10}   Up: ${upspeed wlan0} ${alignr}${upspeedgraph wlan0 10,100 000000 000000}
${color yellow}${font Pie charts for maps:size=10}   Down: ${downspeed wlan0} ${alignr}${downspeedgraph wlan0 10,100 000000 000000}
${color yellow}${font Pie charts for maps:size=10}   Upload Total: ${alignr}${totalup wlan0}
${color yellow}${font Pie charts for maps:size=10}   Download Total: ${alignr}${totaldown wlan0}

---

