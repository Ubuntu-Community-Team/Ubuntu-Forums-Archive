---
title: "conky: mobile broadband signal strength please."
date: 2011-11-10
forum: General Help
---

### Post by daniel227 on 2011-11-10
[SIZE=4]hello,

so i have my wonderful conky set up, and now i started using my dongle (huawei e180) again and it seems conky can't read the signal strength. 
i replaced wlan0 with ppp0 - up, down and ip show, but not signal strength.

mayb i'd have to replace wireless_link_qual with sth else?

here's the relevant bit of code:

[/SIZE]```
${alignc 10}${font PF Tempesta Seven Extended:size=6:style=bold}- I N T E R N E T -${font}

Up: ${upspeed ppp0} ${alignr}${upspeedgraph ppp0 8,60 000000 000000}
Down: ${downspeed ppp0} ${alignr}${downspeedgraph ppp0 8,60 000000 000000}
#Upload: ${alignr}${totalup ppp0}
#${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown ppp0}
Signal: ${wireless_link_qual ppp0}% ${alignr}${wireless_link_bar 8,60 ppp0}
Local Ip: ${alignr}${addr ppp0}

```[SIZE=4]any help is appreciated. thx[/SIZE]

---

### Post by daniel227 on 2011-11-13
anybody?

what would be the right place to ask?

---

### Post by Dr.Aequitas on 2012-04-07
Have you found any solution yet? I'm also trying to find out the same thing.

---

