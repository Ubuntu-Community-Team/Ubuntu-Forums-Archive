---
title: "need usage guage"
date: 2010-06-29
forum: General Help
---

### Post by mike555 on 2010-06-29
My ISP just got a 10 GB cap so I want a GUI gauge to tell me my usage for the month , I have tried some but they rely on a static address , which I don't have........ any suggestions ??
  I would change ISP but none around ........

---

### Post by jondodson on 2010-06-29
I use knemo.  It sits in the tray and monitors daily, monthly and yearly throughput.  It also looks like the windows networking icon in that it animates when data is being received/sent.

---

### Post by mike555 on 2010-06-29
Thanks , but I really don't want to install a bunch of KDE stuff , I was hoping for something for Gnome...

---

### Post by mike555 on 2010-06-30
Bump

---

### Post by stinkeye on 2010-06-30
Have a look at vnstat [**_https://help.ubuntu.com/community/HowToMonitorInternetTrafficTotals_**]("https://help.ubuntu.com/community/HowToMonitorInternetTrafficTotals")

and using it with conky [**_http://conky.linux-hardcore.com/beginners/programs/using-vnstat/_**]("http://conky.linux-hardcore.com/beginners/programs/using-vnstat/")


Here's a simple conky config you could use.
The totals in the pic are all the same because I only just installed vnstat to test it.
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
alignment top_right
gap_x 10
gap_y 35
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

TEXT
${goto 90}${color1}${font DejaVu Sans Mono:bold:size=12}INTERNET USAGE
${goto 90}${font DejaVu Sans Mono:bold:size=10}${color3}Down${goto 160}${color9}Up${goto 230}${color5}Total
${goto 10}${font DejaVu Sans Mono:bold:size=9}${color1}Yesterday: ${color3} ${execi 300 vnstat | grep "yesterday" | awk '{print $2 $3}'}${goto 160}${color9}${execi 300 vnstat | grep "yesterday" | awk '{print $5 $6}'}${goto 230}${color5}${execi 300 vnstat | grep "yesterday" | awk '{print $8 $9}'}
${goto 10}    ${color1}Today: ${color3}${execi 300 vnstat | grep "today" | awk '{print $2 $3}'}${goto 160}${color9}${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}${goto 230}${color5}${execi 300 vnstat | grep "today" | awk '{print $8 $9}'}
${goto 10}     ${color1}Week: ${color3}${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'}${goto 160}${color9}${execi 300 vnstat -w | grep "current week" | awk '{print $6 $7}'}${goto 230}${color5}${execi 300 vnstat -w | grep "current week" | awk '{print $9 $10}'}
${goto 10}    ${color1}Month: ${color3}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${goto 160}${color9}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}${goto 230}${color5}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $9 $10}'}${font}
```

---

### Post by justleen on 2010-06-30
vnstat is the way to go I'd say, as the poster above points out.

---

