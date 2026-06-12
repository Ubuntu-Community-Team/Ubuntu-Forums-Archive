---
title: "need a little help with conky"
date: 2011-05-13
forum: General Help
---

### Post by debd on 2011-05-13
I've been trying to set up a simpler conky this time and tried to avoid keeping its own window, as it looks a bit ugly to my eyes.
Following is my conky script.
The problem is, when I run this script, any  other icons on the desktop is not shown anymore. They are shown only when hovering the mouse pointers over those icons.
What parameter should I add to the script?
Also, their's something weird with ${alignr} ...uh..I had to set different values for them to keep things aligned. Am I missing something?

```
######################
# - Conky settings - #
######################
background yes
alignment top_right
update_interval 1
total_run_times 0
net_avg_samples 1
cpu_avg_samples 1

imlib_cache_size 0
double_buffer yes
no_buffers yes
#no_buffers yes

#####################
# - Text settings - #
#####################
use_xft yes
xftfont Ubuntu:size=8
override_utf8_locale yes
text_buffer_size 2048

#############################
# - Window specifications - #
#############################
own_window_class Conky
own_window no
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
use_spacer none
#own_window_type conky
#own_window_transparent yes
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#own_window_argb_visual yes
#own_window_argb_value 100

#alignment top_right
gap_x 12
gap_y 48
minimum_size 190 180


default_bar_size 60 8

#########################
# - Graphics settings - #
#########################
draw_shades no

default_color efefef
default_shade_color 1d1d1d
color0 ffffff
color1 ffffff
color2 ffffff


#lua_load ~/.conky/conkybg.lua
#lua_draw_hook_pre conky_draw_bg

TEXT

#${voffset 7}${alignc 3}${font Ubuntu:style=Bold:size=9}${time %a - %d %B}${font} ${execi 2000 /home/live/.conkycolors/scripts/conkyForecast.py}
${image ~/.conky/simple/BG.png -p 10,0 -s 181x316}
${alignr 110}${font Ubuntu:style=Bold:size=9}SYSTEM: ${font}

${alignr 38}CPU1: ${font Ubuntu:style=Bold:size=8}${color1}${cpu cpu1}%  ${alignr 20}Temp: ${font Ubuntu:style=Bold:size=9}${color1}${execi 10 sensors|grep "CPU Temperature"|cut -d ":" -f 2|cut -c 6-7}°C${color}${font}  
${alignr 105}CPU2: ${font Ubuntu:style=Bold:size=8}${color1}${cpu cpu2}%
#${goto 40}CPU2: ${font Ubuntu:style=Bold:size=8}${color1}${cpu cpu2}%${font} ${alignr 25}${font Ubuntu:style=Bold:size=9}${color1}${execi 30 sensors | grep 'Core1' | cut -c15-16}°C${color}${font}  

${alignr 100}RAM: ${font Ubuntu:style=Bold:size=8}${memperc}%${font} 

${alignr 47}F: ${color2}${font Ubuntu:style=Bold:size=8}${memeasyfree}${font} ${color} U: ${color2}${font Ubuntu:style=Bold:size=8}${mem}${color}${font} 

${alignr 100}${font Ubuntu:style=Bold:size=9}NETWORK: ${font}

#${if_up eth1}
${alignr 93}${font PizzaDude Bullets:size=11}v${font} Up: ${font Ubuntu:style=Bold:size=9}${color1}${upspeed eth1}${color}${font}
${alignr 59}${font PizzaDude Bullets:size=11}M${font} TotalUp: ${font Ubuntu:style=Bold:size=8}${color2}${totalup eth1}${color}${font} 

${alignr 80}${font PizzaDude Bullets:size=11}r${font} Down: ${font Ubuntu:style=Bold:size=9}${color1}${downspeed eth1}${color}${font}
${alignr 48}${font PizzaDude Bullets:size=11}S${font} TotalDown: ${font Ubuntu:style=Bold:size=8}${color2}${totaldown eth1}${color}${font} 

#${goto 40}Signal: ${font Ubuntu:style=Bold:size=9}${color1}${wireless_link_qual eth1}%${color}${font} ${alignr 15}
```

---

### Post by stinkeye on 2011-05-13
Use
```
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
``` 
Make sure you delete any conflicting values in your config.

Instead of using ${alignr 110} or similar use ${goto xx} with
xx being the pixel distance from the left side of your conky.

You only want to use **alignr** when you want that output to be on the righthand side of your conky.

eg if you have a conky 200 wide
${alignr 110} is the same as ${goto 90}
${alignr 110} aligns on the right and then brings it in 110 from the right side.

eg something like this
```
######################
# - Conky settings - #
######################
background yes
alignment top_right
update_interval 1
total_run_times 0
net_avg_samples 1
cpu_avg_samples 1

imlib_cache_size 0
double_buffer yes
no_buffers yes
#no_buffers yes

#####################
# - Text settings - #
#####################
use_xft yes
xftfont Ubuntu:size=8
override_utf8_locale yes
text_buffer_size 2048

#############################
# - Window specifications - #
#############################

own_window yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
use_spacer right
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#own_window_argb_visual yes
#own_window_argb_value 100

#alignment top_right
gap_x 12
gap_y 48
minimum_size 200 180


default_bar_size 60 8

#########################
# - Graphics settings - #
#########################
draw_shades no

default_color efefef
default_shade_color 1d1d1d
color0 ffffff
color1 ffffff
color2 ffffff


#lua_load ~/.conky/conkybg.lua
#lua_draw_hook_pre conky_draw_bg

TEXT
${image ~/.conky/simple/BG.png -p 10,0 -s 181x316}
${goto 10}${font Ubuntu:style=Bold:size=9}SYSTEM: ${font}

${goto 20}CPU1: ${font Ubuntu:style=Bold:size=8}${color1}${cpu cpu1}%${alignr}Temp: ${font Ubuntu:style=Bold:size=9}${color1}${execi 10 sensors|grep "CPU Temperature"|cut -d ":" -f 2|cut -c 6-7}°C${color}${font}  
${goto 20}CPU2: ${font Ubuntu:style=Bold:size=8}${color1}${cpu cpu2}%
#${goto 40}CPU2: ${font Ubuntu:style=Bold:size=8}${color1}${cpu cpu2}%${font} ${alignr 25}${font Ubuntu:style=Bold:size=9}${color1}${execi 30 sensors | grep 'Core1' | cut -c15-16}°C${color}${font}  

${goto 10}RAM: ${font Ubuntu:style=Bold:size=8}${memperc}%${font} 

${goto 20}F: ${color2}${font Ubuntu:style=Bold:size=8}${memeasyfree}${font} ${color} U: ${color2}${font Ubuntu:style=Bold:size=8}${mem}${color}${font} 

${goto 10}${font Ubuntu:style=Bold:size=9}NETWORK: ${font}

#${if_up eth1}
${goto 20}${font PizzaDude Bullets:size=11}v${font}Up:${alignr}${font Ubuntu:style=Bold:size=9}${color1}${upspeed eth1}${color}${font}
${goto 20}${font PizzaDude Bullets:size=11}M${font} TotalUp: ${alignr}${font Ubuntu:style=Bold:size=9}${color2}${totalup eth1}${color}${font}

${goto 20}${font PizzaDude Bullets:size=11}r${font}Down:${alignr}${font Ubuntu:style=Bold:size=9}${color1}${downspeed eth1}${color}${font}
${goto 20}${font PizzaDude Bullets:size=11}S${font}TotalDown:${alignr}${font Ubuntu:style=Bold:size=9}${color2}${totaldown eth1}${color}${font}

#${goto 40}Signal: ${font Ubuntu:style=Bold:size=9}${color1}${wireless_link_qual eth1}%${color}${font} ${alignr 15}
```

---

### Post by debd on 2011-05-14
Well, I reformatted the script..
The wiping-icons problem is solved, but I dont get the curvature at the end..actually the picture isn't displayed upto the last point :(


```
######################
# - Conky settings - #
######################
background yes
alignment top_right
update_interval 1
total_run_times 0
net_avg_samples 1
cpu_avg_samples 1

imlib_cache_size 0
double_buffer yes
no_buffers yes
#no_buffers yes

#####################
# - Text settings - #
#####################
use_xft yes
xftfont Ubuntu:size=9
override_utf8_locale yes
text_buffer_size 2048

#############################
# - Window specifications - #
#############################

own_window yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
use_spacer right
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
default_shade_color grey
default_outline_color black
#own_window_argb_visual yes
#own_window_argb_value 100

#alignment top_right
gap_x 12
gap_y 48
minimum_size 200 180


default_bar_size 60 8

#########################
# - Graphics settings - #
#########################
draw_shades no

default_color efefef
default_shade_color 1d1d1d
color0 ffffff
color1 ffffff
color2 ffffff


#lua_load ~/.conky/conkybg.lua
#lua_draw_hook_pre conky_draw_bg

TEXT
${image ~/.conky/simple/BG.png -p 10,0 -s 181x316}
${goto 35}${font Ubuntu:style=Bold:size=9}SYSTEM: ${font}

${goto 35}CPU1: ${font Ubuntu:style=Bold:size=8}${color1}${cpu cpu1}%${alignr 30 30}Temp: ${font Ubuntu:style=Bold:size=9}${color1}${execi 10 sensors|grep "CPU Temperature"|cut -d ":" -f 2|cut -c 6-7}°C${color}${font}  
${goto 35}CPU2: ${font Ubuntu:style=Bold:size=8}${color1}${cpu cpu2}%
#${goto 35}CPU2: ${font Ubuntu:style=Bold:size=8}${color1}${cpu cpu2}%${font} ${alignr 30 25}${font Ubuntu:style=Bold:size=9}${color1}${execi 35 sensors | grep 'Core1' | cut -c15-16}°C${color}${font}  

${goto 35}RAM: ${font Ubuntu:style=Bold:size=8}${memperc}%${font} 

${goto 35}F: ${color2}${font Ubuntu:style=Bold:size=8}${memeasyfree}${font}${color} U: ${color2}${font Ubuntu:style=Bold:size=8}${mem}${color}${font} 

${goto 35}${font Ubuntu:style=Bold:size=9}NETWORK: ${font}

#${if_up eth1}
${goto 35}${font PizzaDude Bullets:size=11}v${font}Up:${alignr 43}${font Ubuntu:style=Bold:size=9}${color1}${upspeed eth1}${color}${font}
${goto 35}${font PizzaDude Bullets:size=11}M${font} TotalUp: ${alignr 43}${font Ubuntu:style=Bold:size=9}${color2}${totalup eth1}${color}${font}

${goto 35}${font PizzaDude Bullets:size=11}r${font}Down:${alignr 43}${font Ubuntu:style=Bold:size=9}${color1}${downspeed eth1}${color}${font}
${goto 35}${font PizzaDude Bullets:size=11}S${font}TotalDown:${alignr 43}${font Ubuntu:style=Bold:size=9}${color2}${totaldown eth1}${color}${font}

#${goto 40}Signal: ${font Ubuntu:style=Bold:size=9}${color1}${wireless_link_qual eth1}%${color}${font} ${alignr 30 15} 
```

---

### Post by stinkeye on 2011-05-14
> **debd said:**
> Well, I reformatted the script..
The wiping-icons problem is solved, but I dont get the curvature at the end..actually the picture isn't displayed upto the last point :(




As the [COLOR="#ff00ff"]height[/COLOR] of the backgound image your loading with ${image ~/.conky/simple/BG.png -p 10,0 -s 181x[COLOR="Magenta"]316[/COLOR]}
is [COLOR="Magenta"]316[/COLOR],
set the minimum height of your conky by changing
```
minimum_size 200 [COLOR="#ff00ff"]180[/COLOR]
```


to
```
minimum_size 200 [COLOR="Magenta"]320[/COLOR]
```

---

### Post by debd on 2011-05-14
Ooh..  Thanks!

that's exactly what I wanted.

but one thing still bugs me: when I add conky to my startup apps, the conky window always stays on top of all other windows. But when starting manually, there's no problem.

What might be the problem?
I'm suspecting that setting the window type to 'override' might be causing this.

---

### Post by stinkeye on 2011-05-14
> **debd said:**
> Ooh..  Thanks!

that's exactly what I wanted.

but one thing still bugs me: when I add conky to my startup apps, the conky window always stays on top of all other windows. But when starting manually, there's no problem.

What might be the problem?
I'm suspecting that setting the window type to 'override' might be causing this.

You need to delay the start of conky until your window manager has loaded.

Add this as the command in startup applications if your conky is saved as
**.conkyrc** in your home folder
```
bash -c "sleep 15 && conky"
```


otherwise use
```
bash -c "sleep 15 && conky -c [COLOR="Magenta"]/path/to/your/conkyconfig[/COLOR]"
```
Change to [COLOR="#ff00ff"]wherever you saved your config[/COLOR]

You may be able to reduce the sleep time depending on how fast your desktop loads.

---

### Post by debd on 2011-05-14
Thanks.
I'll try this.

For now, I'll mark this thread as solved.

---

### Post by KrisDeniseRiley1 on 2012-01-06
Hey, I am looking for some help with conky script. I have version 1.8.1, which I am finding to be a pain. I do not know much about python or conky scripting, but I can get around a little bit. I am running my script on Ubuntu 11.10. I can not seem to get my essid or bitrate to show up at all in the script. This is what I got. Any help would be nice. Oh, my wireless interface comes up as eth1.

```
use_xft yes
xftfont verdana:size=8
alignment top_left
xftalpha 0.8
own_window class Conky
own_window yes
#own_window_type override
own_window_type conky
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 4D6844

color0 E6E6E6
color1 A7CC5C
color2 E6E6E6

override_utf8_locale yes



#border_inner_margin 0
#border_outer_margin 0

minimum_size 310 310
maximum_width 310
    

#alignment tl
gap_x -20
gap_y 40

# -- Graphics settings -- #
#draw_graph_borders yes

# -- Text settings -- #
use_xft yes
#xftfont MaiandraGD:size=24
#xftalpha 0.4

#default_color 8b8b8b



TEXT
#######################################
###             Logo              #####
#######################################
#${color D3DADF}${font OpenLogos:size=40}   S  
#######################################
###         HTC Weather            ####
#######################################  
${voffset 30}${font Helvetica LT Std :style=Condensed:size=60}${color 434343}${goto 42}${time %H}${goto 142}${color 434343}${time %M}${font Helvetica LT Std :size=15:style=condensed}${color 808080}${goto 229}${time %S}
${voffset 55}${color whitesmoke}${font Helvetica LT Std :size=8}${alignr 105}${time %A},${time %e},${time %B},${time %G}
${voffset -45}${goto 22}${font Helvetica LT Std :size=8}${color 909090}${execi 600 conkyForecast -i --location=USOR0304 --datatype=CN --refetch}
#${voffset 8}${font Helvetica LT Std :size=10}${color 707070}${goto 24}&#1041;&#1091;&#1088;&#1075;&#1072;&#1089;
${font Helvetica LT Std :size=8}${color whitesmoke}${goto 24}${execi 1800 conkyForecast -i --location=USOR0304 --datatype=CT}${voffset -10}${goto 200}${font Helvetica LT Std :size=25}${color d4d4d4}${execi 1800 conkyForecast -i --location=USOR0304 -u
--datatype=HT}
${voffset 35}${font Helvetica LT Std :size=8}${color white}${goto 34}${execi 600 conkyForecast -i --location=USOR0304 --datatype=HT -u --startday=1}/${color 707070}${execi 600 conkyForecast -i --location=USOR0304 --datatype=LT -u --startday=1}${font Helvetica LT Std :size=8}${color white}${goto 79}${execi 600 conkyForecast -i --location=USOR0304 --datatype=HT -u --startday=2}/${color 707070}${execi 600 conkyForecast -i --location=USOR0304 --datatype=LT -u --startday=2}${font Helvetica LT Std :size=8}${color white}${goto 128}${execi 600 conkyForecast -i --location=USOR0304 --datatype=HT -u --startday=3}/${color 707070}${execi 600 conkyForecast -i --location=USOR0304 --datatype=LT -u --startday=3}${font Helvetica LT Std :size=8}${color white}${goto 169}${execi 600 conkyForecast -i --location=USOR0304 --datatype=HT -u --startday=4}/${color 707070}${execi 600 conkyForecast -i --location=USOR0304 --datatype=LT -u --startday=4}
${font Helvetica LT Std :size=8}${color 707070}${goto 34}${execi 600 conkyForecast -i --location=USOR0304 --datatype=DW --shortweekday --startday=1}${font Helvetica LT Std :size=8}${color 707070}${goto 79}${execi 600 conkyForecast -i --location=USOR0304 --datatype=DW --shortweekday --startday=2}${font Helvetica LT Std :size=8}${color 707070}${goto 120}${execi 600 conkyForecast -i --location=USOR0304 --datatype=DW --shortweekday --startday=3}${font Helvetica LT Std :size=8}${color 707070}${goto 169}${execi 600 conkyForecast -i --location=USOR0304 --datatype=DW --shortweekday --startday=4}
${voffset -10}${font Helvetica LT Std :size=8}${color 707070}${goto 216}${execi 600 conkyForecast -i --location=USOR0304 --datatype=DW --shortweekday --startday=5}
${voffset -23}${font Helvetica LT Std :size=8}${color white}${goto 216}${execi 600 conkyForecast -i --location=USOR0304 --datatype=HT -u --startday=5}/${color 707070}${execi 600 conkyForecast -i --location=USOR0304 --datatype=LT -u --startday=5}
${image /home/kris/.images/base.png -p 12,30 -s 238x140}
${image /home/kris/.images/base.png -p 12,190 -s 238x40}
${image /home/kris/.images/flip_bg.png -p 30,10 -s 100x110}
${image /home/kris/.images/flip_bg.png -p 130,10 -s 100x110}
${execpi 600 conkyForecast -i --location=USOR0304 --template=/home/kris/.vreme.template}
####################################
###          Email Setup        ####
####################################
${voffset -32}${color black}${font OpenLogos:size=46}S${color gray}${font WW2 BlackltrAlt:size=22}Current Emails & PC Vitals${color white}
${color lightgrey}${hr 2}
${voffset -9}${font OpenLogos:size=38}J${font Radio Space:size=22}${color yellow}${execpi 300 python ~/scripts/gmail_parser.py hornerkris@gmail.com June10th 3}${font Radio Space:size=14}${color 014A7F} New Message(s)
####################################
###       Battery Bar           ####
####################################
${color lightgrey}${font OpenLogos:size=26}T${color 014A7F}${font}  Battery: ${battery_percent}% ${battery_bar}
${color ffffff}${color lightgrey}${font OpenLogos:size=26}K${color 014A7F}${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
${color lightgrey}${font OpenLogos:size=26}K${color 014A7F}${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}
${color lightgrey}${font OpenLogos:size=30}t${color 014A7F}${font}  Work:  ${uptime_short}
####################################
###         Network Info        ####
####################################
${font WW2 BlackltrAlt:size=22}Network Info${color black}${hr 2}
#${voffset -32}${color black}${font Poky:size=44}Y${color gray}
${image /home/kris/.images/wlanbg2.png  -s 400x140 -p -50,565}
${offset 15}${alignc}${execp /home/kris/wlanscript.sh}

${voffset -105}${color black}${font WW2 BlackltrAlt:size=13}${alignc -20}SSID: ${wireless_essid wlan0}
${alignc -20}Bitrate: ${wireless_bitrate eth1}
${alignc -50}Local: ${addr eth1}
${alignc -58}Public: ${execi 300 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
${voffset -25}${offset 25}${wireless_link_qual wlan0}%

${voffset 4}${font PizzaDude Bullets:size=14}Z${font} Signal: ${wireless_link_qual eth1}% ${alignr}${wireless_link_bar 8,60 eth1}


 
```

I know it is a little bit messy, but I have been doing a little experimenting. Please help me with the bitrate and ssid PLEASE!!!!

---

### Post by debd on 2012-01-08
[@KrisDeniseRiley1]("http://ubuntuforums.org/member.php?u=1475424")
well bud, wireless interfaces are generally named wlanX i.e wlan0 , wlan1 and so on..
so just run ```
ifconfig
``` in a terminal and see which interface has your current ip address and replace with that in the conky script. 
I hope that'll help.

---

