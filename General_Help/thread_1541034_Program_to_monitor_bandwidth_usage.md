---
title: "Program to monitor bandwidth usage?"
date: 2010-07-28
forum: General Help
---

### Post by leucippus on 2010-07-28
Hey guys...I live in the boonies, so I have satellite internet. It's not too bad, but I'm restricted to 200 mb's of download per day. 

  I'm looking for an app that will keep track of my usage, so I don't go over 200. I was using "System Monitor", but it's a little buggy, so I'd like to try something else. Thanks :D

---

### Post by davidmohammed on 2010-07-28
... little [old]("http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html") - but worth a read.

---

### Post by leucippus on 2010-07-28
Thanks...great link! Looks like IBMonitor will do the trick. With the terminal up, just press "d" to get the cumulative tally for the session. :D

---

### Post by BenAshton24 on 2010-07-28
I prefer vnStat: [http://humdi.net/vnstat/](http://humdi.net/vnstat/)

---

### Post by leucippus on 2010-07-28
I tried Vnstat, but I couldn't get it to run. Here's a screenie of my terminal. :(

---

### Post by stinkeye on 2010-07-28
```
sudo vnstat -u -i eth0
```
to create a database.


then```
vnstat
```

You can use conky to display vnstat data.
```
sudo apt-get install conky
```

Save this config in your home folder as **.conkyrc**
```
background yes
font Sans Seriff:size=9
xftfont DejaVu Sans Mono:bold:size=10
use_xft yes
xftalpha 0.8
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 300
maximum_width 300
default_color 919FAA
default_shade_color 333333
default_outline_color 00ff00
alignment br
gap_x 10
gap_y 10
no_buffers yes
cpu_avg_samples 2
override_utf8_locale yes
uppercase no # set to yes if you want all text to be in uppercase
use_spacer right

# colours
#off white
color1 BDAC88

# cream
color2 D2B16A

# cyan
#color3 08A1A1

# bluemoon
color3 919FAA

# yellow
color4 F1BC49

# Green
color5 00940F

#dark cyan
color6 074C4C


#grey
color7 6b6b6b

#orange
color8 AF560D

#yellow
color9 F1BC49

#lua_load /home/glen/conky/draw_bg.lua
#lua_draw_hook_pre draw_bg

TEXT
${goto 90}${color1}${font DejaVu Sans Mono:bold:size=12}INTERNET USAGE
${goto 90}${voffset -15}______________
${goto 90}${font DejaVu Sans Mono:bold:size=10}${color3}Down${goto 170}${color9}Up${goto 235}${color5}Total
${goto 10}${font DejaVu Sans Mono:bold:size=9}${color1}Yesterday: ${color3}${execi 300 vnstat | grep "yesterday" | awk '{print $2 $3}'}${goto 170}${color9}${execi 300 vnstat | grep "yesterday" | awk '{print $5 $6}'}${goto 235}${color5}${execi 300 vnstat | grep "yesterday" | awk '{print $8 $9}'}
${goto 10}    ${color1}Today: ${color3}${execi 300 vnstat | grep "today" | awk '{print $2 $3}'}${goto 170}${color9}${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}${goto 235}${color5}${execi 300 vnstat | grep "today" | awk '{print $8 $9}'}
${goto 10}     ${color1}Week: ${color3}${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'}${goto 170}${color9}${execi 300 vnstat -w | grep "current week" | awk '{print $6 $7}'}${goto 235}${color5}${execi 300 vnstat -w | grep "current week" | awk '{print $9 $10}'}
${goto 10}    ${color1}Month: ${color3}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${goto 170}${color9}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}${goto 235}${color5}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $9 $10}'}${font}
``` 


Alt+F2 and run **conky**
and you should see the attached pic in the bottom right corner.

---

### Post by leucippus on 2010-07-28
> **stinkeye said:**
> 

Alt+F2 and run **conky**
and you should see the attached pic in the bottom right corner.

 Yu da man! :guitar:

---

### Post by stinkeye on 2010-07-28
> **leucippus said:**
> Yu da man! :guitar:
Haha, I'm D'oh man. #-o

---

