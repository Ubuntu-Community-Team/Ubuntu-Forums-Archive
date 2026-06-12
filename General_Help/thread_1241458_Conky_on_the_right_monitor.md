---
title: "Conky on the right monitor"
date: 2009-08-16
forum: General Help
---

### Post by xenogia on 2009-08-16
Currently I purchased a dual monitor and I am wondering how to go about changing the script so it displays on the right monitor at the upper right hand corner.  Here is my script for you to look at.  How do I go about changing it so it works.

```

use_xft yes
xftfont Liberation Candara:size=8

update_interval 1
total_run_times 0
double_buffer yes
text_buffer_size 2048

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

minimum_size 185 0
maximum_width 185

default_color white
draw_shades no

color0 white
color1 red
color2 white

alignment top_right
gap_x 25
gap_y 50

no_buffers no
net_avg_samples 2

override_utf8_locale yes

no_buffers yes

TEXT
SYSTEM ${hr 2}
${voffset 2}${color0}${font OpenLogos:size=16}u${font}${color}   Kernel:  ${alignr}${color2}${kernel}${color}
${color0}${font StyleBats:size=16}A${font}${color}   CPU1: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu1}%${color}${font} ${alignr}${color2}${cpubar cpu1 8,60}${color}
${color0}${font StyleBats:size=16}A${font}${color}   CPU2: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu2}%${color}${font} ${alignr}${color2}${cpubar cpu2 8,60}${color}
${color0}${font StyleBats:size=16}A${font}${color}   CPU3: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu3}%${color}${font} ${alignr}${color2}${cpubar cpu3 8,60}${color}
${color0}${font StyleBats:size=16}A${font}${color}   CPU4: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu4}%${color}${font} ${alignr}${color2}${cpubar cpu4 8,60}${color}
${color0}${font StyleBats:size=16}g${font}${color}   RAM: ${font Liberation Sans:style=Bold:size=8}${color1}$memperc%${color}${font} ${alignr}${color2}${membar 8,60}${color}
${color0}${font StyleBats:size=16}j${font}${color}   SWAP: ${font Liberation Sans:style=Bold:size=8}${color1}$swapperc%${color}${font} ${alignr}${color2}${swapbar 8,60}${color}
${color0}${font StyleBats:size=16}q${font}${color}   Uptime: ${alignr}${color2}${uptime}${color}
${color0}${font StyleBats:size=16}l${font}${color}   Processes: ${color2}${alignr 13}CPU${alignr}RAM${color}
${goto 32}${top name 1}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 1}${alignr }${top mem 1}${color}${font}
${goto 32}${top name 2}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 2}${alignr }${top mem 2}${color}${font}
${goto 32}${top name 3}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 3}${alignr }${top mem 3}${color}${font}
${goto 32}${top name 4}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 4}${alignr }${top mem 4}${color}${font}
${goto 32}${top name 5}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 5}${alignr }${top mem 5}${color}${font}

DATE ${hr 2}
${voffset 10}${alignc 55}${font aClock:style=_Hour:size=90}${color2}${execi 120 python ~/.scripts/conkyClock_h.py}${color}${font}
${voffset -98}${alignc 55}${font aClock:style=_Min:size=90}${color2}${execi 60 python ~/.scripts/conkyClock_m.py}${color}${font}
${voffset 12}${alignc}${font Liberation Sans:style=Bold:size=10}${color1}${time %H:%M}${color}${font}${voffset -8}
${voffset 8}${alignc}${time %A %d %Y}
HD ${hr 2}
${execpi 30 ~/.scripts/hd_default.py}

NETWORK ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -6}${color0}${font PizzaDude Bullets:size=14}O${font}${color}   Up: ${font Liberation Sans:style=Bold:size=8}${color1}${upspeed wlan0}${color}${font} kb/s ${alignr}${upspeedgraph wlan0 8,60 77507b ad7fa8}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}U${font}${color}   Down: ${font Liberation Sans:style=Bold:size=8}${color1}${downspeed wlan0}${color}${font} kb/s ${alignr}${downspeedgraph wlan0 8,60 77507b ad7fa8}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}N${font}${color}   Upload: ${alignr}${totalup wlan0}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}T${font}${color}   Download: ${alignr}${totaldown wlan0}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}Z${font}${color}   Signal: ${font Liberation Sans:style=Bold:size=8}${color1}${wireless_link_qual wlan0}%${color}${font} ${alignr}${color2}${wireless_link_bar 8,60 wlan0}${color}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}a${font}${color}   Local ip: ${alignr}${color2}${addr wlan0}${color}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}b${font}${color}   Public ip: ${alignr}${color2}${execi 10800 ~/.scripts/ip.sh}${color}
${else}${if_existing /proc/net/route eth0}
${voffset -6}${color0}${font PizzaDude Bullets:size=14}O${font}${color}   Up: ${font Liberation Sans:style=Bold:size=8}${color1}${upspeed eth0}${color}${font} kb/s ${alignr}${upspeedgraph eth0 8,60 77507b ad7fa8}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}U${font}${color}   Down: ${font Liberation Sans:style=Bold:size=8}${color1}${downspeed eth0}${color}${font} kb/s ${alignr}${downspeedgraph eth0 8,60 77507b ad7fa8}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}N${font}${color}   Upload: ${alignr}${color2}${totalup eth0}${color}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}T${font}${color}   Download: ${alignr}${color2}${totaldown eth0}${color}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}a${font}${color}   Local ip: ${alignr}${color2}${addr eth0}${color}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}b${font}${color}   Public ip: ${alignr}${color2}${execi 10800 ~/.scripts/ip.sh}${color}
${endif}${else}${if_existing /proc/net/route ppp0}
${voffset -6}${color0}${font PizzaDude Bullets:size=14}O${font}${color}   Up: ${font Liberation Sans:style=Bold:size=8}${color1}${upspeed ppp0}${color}${font} kb/s ${alignr}${upspeedgraph ppp0 8,60 77507b ad7fa8}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}U${font}${color}   Down: ${font Liberation Sans:style=Bold:size=8}${color1}${downspeed ppp0}${color}${font} kb/s ${alignr}${downspeedgraph ppp0 8,60 77507b ad7fa8}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}N${font}${color}   Upload: ${alignr}${color2}${totalup ppp0}${color}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}T${font}${color}   Download: ${alignr}${color2}${totaldown ppp0}${color}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}a${font}${color}   Local ip: ${alignr}${color2}${addr ppp0}${color}
${endif}${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}   Network Unavailable
${endif}

```

---

### Post by PurposeOfReason on 2009-08-16
You have to say which display to start on like this:

DISPLAY=:0.1 conky

---

### Post by xenogia on 2009-08-16
> **PurposeOfReason said:**
> You have to say which display to start on like this:

DISPLAY=:0.1 conky

So do you put that at the start of the script?

---

### Post by PurposeOfReason on 2009-08-16
> **xenogia said:**
> So do you put that at the start of the script?
No, that is how you run conky to start instead of just typing 'conky'.

---

