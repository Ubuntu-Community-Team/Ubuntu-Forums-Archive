---
title: "Bandwidth meter for 10.10"
date: 2011-11-21
forum: General Help
---

### Post by meetdilip on 2011-11-21
Just need to know how much is the download and upload speed. Please recommend one with a graphical interface.

---

### Post by meetdilip on 2011-11-23
No one ?

---

### Post by crazy bird on 2011-11-23
Go to synaptic and search for **netspeed**.
Install it and then on the top panel or bottom panel rigth click, click on *add to panel* and search for netspeed. It will appear on the toolbar and shows the upload and download speed. 

Here are some links:
[http://www.ubuntugeek.com/netspeed-traffic-monitor-applet-for-gnome.html](http://www.ubuntugeek.com/netspeed-traffic-monitor-applet-for-gnome.html)
[https://launchpad.net/ubuntu/+source/netspeed](https://launchpad.net/ubuntu/+source/netspeed)

---

### Post by coldraven on 2011-11-23
conky? I don't have it installed ATM.

---

### Post by KingYaba on 2011-11-23
+1 on the conky suggestion. 


Here's an example. Punch this into your conky.conf file: 
```
${color white}NETWORK (${addr wlan0}) ${hr 2}$color
Down: $color${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,140 000000 ff0000} ${alignr}${upspeedgraph wlan0
25,140 000000 00ff00}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
```

You may need to change the wlan0 component depending on how you connect to the internet.

---

### Post by OrangeCrate on 2011-11-23
> **meetdilip said:**
> Just need to know how much is the download and upload speed. Please recommend one with a graphical interface.

Several suggestions here:

[http://ubuntuforums.org/showthread.php?t=363602](http://ubuntuforums.org/showthread.php?t=363602)

---

### Post by meetdilip on 2011-11-23
> **crazy bird said:**
> Go to synaptic and search for **netspeed**.
Install it and then on the top panel or bottom panel rigth click, click on *add to panel* and search for netspeed. It will appear on the toolbar and shows the upload and download speed. 

Here are some links:
[http://www.ubuntugeek.com/netspeed-traffic-monitor-applet-for-gnome.html](http://www.ubuntugeek.com/netspeed-traffic-monitor-applet-for-gnome.html)
[https://launchpad.net/ubuntu/+source/netspeed](https://launchpad.net/ubuntu/+source/netspeed)

Thanks, it is working fine. :)

> **coldraven said:**
> conky? I don't have it installed ATM.

> **KingYaba said:**
> +1 on the conky suggestion. 


Here's an example. Punch this into your conky.conf file: 
```
${color white}NETWORK (${addr wlan0}) ${hr 2}$color
Down: $color${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,140 000000 ff0000} ${alignr}${upspeedgraph wlan0
25,140 000000 00ff00}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
```You may need to change the wlan0 component depending on how you connect to the internet.

> **OrangeCrate said:**
> Several suggestions here:

[http://ubuntuforums.org/showthread.php?t=363602](http://ubuntuforums.org/showthread.php?t=363602)

Thanks all :)

---

