---
title: "Conky Length/Width problem"
date: 2011-05-05
forum: General Help
---

### Post by sbjaved on 2011-05-05
Hi.

My conky config which I copied from another machine shows up totally warbled on my laptop. I've attached the conkyrc and screenshot after trying my best to edit it myself. 

I just want these weird alphabets infront of entries removed and the length of the window increased. And text overlapping to be fixed.

Any help would be very welcome as I love my conky :D

Thanks```


######################
# - Conky settings - #
######################
update_interval 1
total_run_times 0
net_avg_samples 1
cpu_avg_samples 1

imlib_cache_size 0
double_buffer yes
no_buffers yes

format_human_readable

#####################
# - Text settings - #
#####################
use_xft yes
xftfont Droid Sans:size=10
override_utf8_locale yes
text_buffer_size 2048

#############################
# - Window specifications - #
#############################
own_window_class Conky
own_window yes
own_window_type normal
own_window_argb_visual yes
own_window_argb_value 180
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

alignment top_right
gap_x 10	
gap_y 10
minimum_size 250 0
maximum_width 250

default_bar_size 60 8

#########################
# - Graphics settings - #
#########################
draw_shades no

default_color 3C3B37

color0 292927
color1 C6B9A6
color2 292927

TEXT
${font Droid Sans:style=Bold:size=8}SYSTEM $stippled_hr${font}
##############
# - SYSTEM - #
##############
${color0}${voffset 6}${font OpenLogos:size=19}u${font}${color}${goto 32}${voffset -14}Kernel:  ${alignr}${color2}${kernel}${color}
${goto 32}Uptime: ${alignr}${color2}${uptime}${color}
# |--CPU
${offset 1}${color0}${font Poky:size=16}P${font}${offset -19}${voffset 9}${cpubar cpu0 4,18}${color}${voffset -16}${goto 32}CPU1: ${font Droid Sans:style=Bold:size=8}${color1}${cpu cpu1}%${font} ${alignr}${font Droid Sans:style=Bold:size=8}${color1}${execi 30 sensors -f | grep 'Core 0' | cut -c14-16}°F${color}${font}  ${color2}${cpugraph cpu1 8,50 C6B9A6 C6B9A6}${color}
${goto 32}CPU2: ${font Droid Sans:style=Bold:size=8}${color1}${cpu cpu2}%${font} ${alignr}${font Droid Sans:style=Bold:size=8}${color1}${execi 30 sensors -f | grep 'Core 1' | cut -c14-16}°F${color}${font}  ${color2}${cpugraph cpu2 8,50 C6B9A6 C6B9A6}${color}
# |--MEM
${color0}${font Poky:size=16}M${font}${color}${goto 32}${voffset -7}RAM: ${font Droid Sans:style=Bold:size=8}${color1}$memperc%${color}${font}
${offset 1}${voffset 2}${color0}${membar 4,18}${color}${goto 32}${voffset -2}F: ${font Droid Sans:style=Bold:size=8}${color2}${memeasyfree}${color}${font} U: ${font Droid Sans:style=Bold:size=8}${color2}${mem}${color}${font}
# |--BATTERY
#${color0}${font Poky:size=13}E${font}${color}${goto 32}${voffset -5}Battery: ${font Droid Sans:style=Bold:size=8}${color1}${battery_percent BAT0}%${color}#${font} ${alignr}${color2}${battery_bar 8,60 BAT0}${color}
# |--PROC
${voffset 2}${color0}${font Poky:size=15}a${font}${color}${goto 32}${voffset -10}Processes: ${color2}${alignr 13}CPU${alignr}RAM${color}
${voffset -1}${goto 42}${color2}${top name 1}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 1}${alignr }${top mem 1}${color}${font}
${voffset -1}${goto 42}${color2}${top name 2}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 2}${alignr }${top mem 2}${color}${font}
${voffset -1}${goto 42}${color2}${top name 3}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 3}${alignr }${top mem 3}${color}${font}
${voffset -1}${goto 42}${color2}${top name 4}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 4}${alignr }${top mem 4}${color}${font}
${voffset -1}${goto 42}${color2}${top name 5}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 5}${alignr }${top mem 5}${color}${font}
${voffset -1}${goto 42}${color2}${top name 6}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 6}${alignr }${top mem 6}${color}${font}
${voffset -1}${goto 42}${color2}${top name 7}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 7}${alignr }${top mem 7}${color}${font}
${voffset -1}${goto 42}${color2}${top name 8}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 8}${alignr }${top mem 8}${color}${font}
${voffset -1}${goto 42}${color2}${top name 9}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 9}${alignr }${top mem 9}${color}${font}
${voffset -1}${goto 42}${color2}${top name 10}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 10}${alignr }${top mem 10}${color}${font}
#############
# - CLOCK - #
#############
${voffset 4}${font Droid Sans:style=Bold:size=8}DATE $stippled_hr${font}
${font Digital Readout Thick Upright:size=40}${goto 2}${color2}${time %k}${voffset -9}:${voffset 9}${time %M}${goto 110}${color2}${voffset -14}${font Digital Readout Thick Upright:size=24}${goto 155}${color2}${time %d}${font Digital Readout Thick Upright:size=12}${voffset 14}${goto 155}${color2}${time %m}/${goto 180}${color2}${time %y}${font}
################
# - CALENDAR - #
################
${voffset -2}${color0}${font Poky:size=16}D${font}${voffset -8}${font Droid Sans:style=Bold:size=7}${offset -17}${voffset 4}${time %d}${font}${color}${voffset -1}${font Droid Sans Mono:size=7}${execpi 300 DJS=`date +%_d`; cal |sed '2,7!d'| sed '/./!d' | sed 's/^/${goto 32} /'| sed 's/$/ /' | sed 's/^/ /' | sed /" $DJS "/s/" $DJS "/" "'${font Droid Sans:style=Bold:size=8}${color1}'"$DJS"'${color}${font Droid Sans Mono:size=7}'" "/}${voffset -1}
##########
# - HD - #
##########
${voffset 4}${font Droid Sans:style=Bold:size=8}HD $stippled_hr${font}
# |--HDTEMP1
  ${voffset 4}${color0}${font Weather:size=15}y${font}${color}${voffset -3}${goto 32}Temperature: ${font Droid Sans:style=Bold:size=8}${color1}${execi 120 hddtemp /dev/sda -n --unit=F}°F${color}${font}${alignr}${color2}/dev/sda${color}
${execpi 30 /usr/share/conkycolors/bin/conkyHD2}
###############
# - NETWORK - #
###############
${voffset 4}${font Droid Sans:style=Bold:size=8}NETWORK $stippled_hr${font}
# |--WLAN0
${if_up wlan0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed wlan0}${color}${font} ${alignr}${color2}${upspeedgraph wlan0 8,60 C6B9A6 C6B9A6}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totalup wlan0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed wlan0}${color}${font} ${alignr}${color2}${downspeedgraph wlan0 8,60 C6B9A6 C6B9A6}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totaldown wlan0}${color}${font}
${voffset -2}${color0}${font Poky:size=14}Y${font}${color}${goto 32} ${voffset -2}Signal: ${font Droid Sans:style=Bold:size=8}${color1}${wireless_link_qual wlan0}%${color}${font} ${alignr}${color2}${wireless_link_bar 8,60 wlan0}${color}
${voffset 4}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -8}Local IP: ${alignr}${color2}${addr wlan0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 /usr/share/conkycolors/bin/conkyIp}${color}
# |--ETH0
${else}${if_up eth0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed eth0}${color}${font} ${alignr}${color2}${upspeedgraph eth0 8,60 C6B9A6 00ff00}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totalup eth0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed eth0}${color}${font} ${alignr}${color2}${downspeedgraph eth0 8,60 C6B9A6 ff0000}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totaldown eth0}${color}${font}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr eth0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 /usr/share/conkycolors/bin/conkyIp}${color}
# |--PPP0
${else}${if_up ppp0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed ppp0}${color}${font} ${alignr}${color2}${upspeedgraph ppp0 8,60 C6B9A6 C6B9A6}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totalup ppp0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed ppp0}${color}${font} ${alignr}${color2}${downspeedgraph ppp0 8,60 C6B9A6 C6B9A6}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totaldown ppp0}${color}${font}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr ppp0}${color}
${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}${goto 32}Network Unavailable${voffset 14}${endif}${endif}${endif}
```

[IMG]https://picasaweb.google.com/lh/photo/trBu_PgWVvZCpXSuGno7VVpHzsJzDldlkD8z9pO312k?feat=directlink[/IMG]
Screenshot URL
[https://picasaweb.google.com/lh/photo/trBu_PgWVvZCpXSuGno7VVpHzsJzDldlkD8z9pO312k?feat=directlink]("https://picasaweb.google.com/lh/photo/trBu_PgWVvZCpXSuGno7VVpHzsJzDldlkD8z9pO312k?feat=directlink")

---

### Post by andrewthomas on 2011-05-05
I didn't see your screenshot for some reason, but I can guess that you need the conkycolors fonts.

[http://gnome-look.org/content/show.php/CONKY-colors?content=92328](http://gnome-look.org/content/show.php/CONKY-colors?content=92328)

You don't need to do all that they tell you on the page.  Just extract the file and copy the font folder to /usr/share/fonts/TTF
then

```
sudo fc-cache -vf
```

Then the Openlogos, Poky,PizzaDude Bullets and other conky fonts will show up.

You also have to change 
```
{execi 10800 /usr/share/conkycolors/bin/conkyIp}
```

to 

```
${execi 10800 wget -O – http://whatismyip.org/ | tail}
```

---

### Post by sbjaved on 2011-05-05
Added the URL to the screenshot. Plz take a look.

---

### Post by andrewthomas on 2011-05-05
First, you need to get the conky fonts into your /usr/share/fonts directory and update the font cache.  

Even if you have followed some of the instructions from the link that I posted.

To get the fonts to work they need to be in either the above fonts directory or in ~/.fonts and the cache has to be updated.

If you download conkycolors and extract the file, then look for the fonts/conkycolors directory.

Copy this to either /usr/share/fonts or ~/.fonts and do:

```
sudo fc-cache -fv
```

after you do that, post another screenshot.

---

### Post by sbjaved on 2011-05-05
the config font is Droid Sans which I installed via synaptic. this very config works perfectly on my desktop so i assume i only need to change some length/width/size values...

---

### Post by sbjaved on 2011-05-06
> **andrewthomas said:**
> First, you need to get the conky fonts into your /usr/share/fonts directory and update the font cache.  

Even if you have followed some of the instructions from the link that I posted.

To get the fonts to work they need to be in either the above fonts directory or in ~/.fonts and the cache has to be updated.

If you download conkycolors and extract the file, then look for the fonts/conkycolors directory.

Copy this to either /usr/share/fonts or ~/.fonts and do:

```
sudo fc-cache -fv
```

after you do that, post another screenshot.
Placed the conky colors fonts in the required directories. That fixed the letters infront problem. Thankyou andrew!

Any suggestion about the overlapping/length issue?

Here the updated photo:
[https://picasaweb.google.com/lh/photo/JCWE78g98BB0Caw9uQwI21pHzsJzDldlkD8z9pO312k?feat=directlink]("https://picasaweb.google.com/lh/photo/JCWE78g98BB0Caw9uQwI21pHzsJzDldlkD8z9pO312k?feat=directlink")

---

### Post by andrewthomas on 2011-05-06
Try changing this in the proc section

```
# |--PROC
${voffset 2}${color0}${font Poky:size=15}a${font}${color}${goto 32}${voffset -10}Processes: ${color2}${alignr 13}CPU${alignr}RAM${color}
${voffset -1}${goto 42}${color2}${top name 1}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 184}${top cpu 1}${alignr }${top mem 1}${color}${font}
${voffset -1}${goto 42}${color2}${top name 2}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 184}${top cpu 2}${alignr }${top mem 2}${color}${font}
${voffset -1}${goto 42}${color2}${top name 3}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 184}${top cpu 3}${alignr }${top mem 3}${color}${font}
${voffset -1}${goto 42}${color2}${top name 4}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 184}${top cpu 4}${alignr }${top mem 4}${color}${font}
${voffset -1}${goto 42}${color2}${top name 5}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 184}${top cpu 5}${alignr }${top mem 5}${color}${font}
${voffset -1}${goto 42}${color2}${top name 6}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 184}${top cpu 6}${alignr }${top mem 6}${color}${font}
${voffset -1}${goto 42}${color2}${top name 7}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 184}${top cpu 7}${alignr }${top mem 7}${color}${font}
${voffset -1}${goto 42}${color2}${top name 8}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 184}${top cpu 8}${alignr }${top mem 8}${color}${font}
${voffset -1}${goto 42}${color2}${top name 9}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 184}${top cpu 9}${alignr }${top mem 9}${color}${font}
${voffset -1}${goto 42}${color2}${top name 10}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 184}${top cpu 10}${alignr }${top mem 10}${color}${font}
```

As to the length, I have no idea why it is getting cut off.  

It should just keep on going, even running off the screen if there are too many lines to display on the screen.

---

### Post by sbjaved on 2011-09-06
I found a solution to my problem. Hope it helps someone. Just change:

own_window_type normal

to

own_window_type **desktop**

---

