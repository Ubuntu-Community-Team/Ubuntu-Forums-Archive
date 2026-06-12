---
title: "Hiding ssid(network name) in conky?"
date: 2009-07-12
forum: General Help
---

### Post by Redundant Username on 2009-07-12
Here is the part of my conky file that concerns me. How do I hide the ssid in conky and change the text to black for that specific area?
```


${if_up wlan0}${color e07401}WIRELESS (IP: ${addr wlan0}- qual: ${wireless_link_qual_perc wlan0}%) ${hr 2}$color
${color A6A6A6}Essid: ${wireless_essid wlan0} ${alignr}Rate: ${wireless_bitrate wlan0}${color}
${color A6A6A6}Down: ${downspeed wlan0} kB/s ${alignr}Up: ${upspeed wlan0} kB/s$color
${color A6A6A6}${downspeedgraph wlan0 25,140 000000 970300} ${alignr}${upspeedgraph wlan0 25,140 000000 297F00}$color
${color A6A6A6}Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan}$color$endif





```

---

### Post by darco on 2009-07-13
> **Redundant Username said:**
> Here is the part of my conky file that concerns me. How do I hide the ssid in conky and change the text to black for that specific area?
```


${if_up wlan0}${color e07401}WIRELESS (IP: ${addr wlan0}- qual: ${wireless_link_qual_perc wlan0}%) ${hr 2}$color
${color A6A6A6}Essid: ${wireless_essid wlan0} ${alignr}Rate: ${wireless_bitrate wlan0}${color}
${color A6A6A6}Down: ${downspeed wlan0} kB/s ${alignr}Up: ${upspeed wlan0} kB/s$color
${color A6A6A6}${downspeedgraph wlan0 25,140 000000 970300} ${alignr}${upspeedgraph wlan0 25,140 000000 297F00}$color
${color A6A6A6}Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan}$color$endif





```

You want to hide it? Why dont you either comment out the line or in your router, choose not to broadcast it?

darco

---

### Post by Redundant Username on 2009-07-13
Nevermind. I figured it out myself and I found out how to change the colors too. I wanted to hide my ssid because it is my last name and I regularly do screen caps.

---

