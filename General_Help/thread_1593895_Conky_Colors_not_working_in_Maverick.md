---
title: "Conky Colors not working in Maverick"
date: 2010-10-11
forum: General Help
---

### Post by ninjapirate89 on 2010-10-11
Has anyone else noticed this when installing conky-colors in Maverick?

[[IMG]http://i1012.photobucket.com/albums/af248/ninjapirate89/th_conky_troubles.png[/IMG]](http://s1012.photobucket.com/albums/af248/ninjapirate89/?action=view&current=conky_troubles.png)

I know its not a problem with how I've configured it because it worked just fine in Lucid but here it is anyway:
```
./conky-colors --lang=english --theme=elementary --cpu=2 --swap --battery --updates --proc=10 --clock=modern --calendar --hd=simple --banshee=simple --network --eth=0 --wlan=0 --side=right --ubuntu
```

If you don't know what conky-colors is, here is a link to it's gnome-look page and an installation tutorial from webupd8.
[http://gnome-look.org/content/show.php/CONKY-colors?content=92328]("http://gnome-look.org/content/show.php/CONKY-colors?content=92328")
[http://www.webupd8.org/2010/07/conky-colors-makes-your-conky-beautiful.html]("http://www.webupd8.org/2010/07/conky-colors-makes-your-conky-beautiful.html")


Edit:
Here is the .conkyrc that is produced in case there is some type of error in it.
```
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
xftfont Droid Sans:size=8
override_utf8_locale yes
text_buffer_size 2048

#############################
# - Window specifications - #
#############################
own_window_class Conky
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

alignment top_right
gap_x 25
gap_y 40
minimum_size 182 0
maximum_width 182

default_bar_size 60 8

#########################
# - Graphics settings - #
#########################
draw_shades no

default_color D6D6D6

color0 FFFFFF
color1 7296BB
color2 FFFFFF

TEXT
${font Droid Sans:style=Bold:size=8}SYSTEM $stippled_hr${font}
##############
# - SYSTEM - #
##############
${color0}${voffset 6}${font OpenLogos:size=19}u${font}${color}${goto 32}${voffset -14}Kernel:  ${alignr}${color2}${kernel}${color}
${goto 32}Uptime: ${alignr}${color2}${uptime}${color}
# |--UPDATES
${goto 32}Updates: ${alignr}${font Droid Sans:style=Bold:size=8}${color1}${execi 360 aptitude search "~U" | wc -l | tail}${color}${font} ${color2}Packages${color}
# |--CPU
${offset 1}${color0}${font Poky:size=16}P${font}${offset -19}${voffset 9}${cpubar cpu0 4,18}${color}${voffset -16}${goto 32}CPU1: ${font Droid Sans:style=Bold:size=8}${color1}${cpu cpu1}%${color}${font} ${alignr}${color2}${cpugraph cpu1 8,60 7296BB 7296BB}${color}
${goto 32}CPU2: ${font Droid Sans:style=Bold:size=8}${color1}${cpu cpu2}%${color}${font} ${alignr}${color2}${cpugraph cpu2 8,60 7296BB 7296BB}${color}
# |--MEM
${color0}${font Poky:size=16}M${font}${color}${goto 32}${voffset -7}RAM: ${font Droid Sans:style=Bold:size=8}${color1}$memperc%${color}${font}
${offset 1}${voffset 2}${color0}${membar 4,18}${color}${goto 32}${voffset -2}F: ${font Droid Sans:style=Bold:size=8}${color2}${memeasyfree}${color}${font} U: ${font Droid Sans:style=Bold:size=8}${color2}${mem}${color}${font}
# |--CPU
${voffset 2}${color0}${font Poky:size=14}s${font}${color}${voffset -8}${goto 32}SWAP: ${font Droid Sans:style=Bold:size=8}${color1}${swapperc}%${color}${font}
${voffset 4}${offset 1}${color0}${swapbar 4,18}${color}${voffset -4}${goto 32}F: ${font Droid Sans:style=Bold:size=8}${color2}$swapmax${color}${font} U: ${font Droid Sans:style=Bold:size=8}${color2}$swap${color}${font}
# |--BATTERY
${color0}${font Poky:size=13}E${font}${color}${goto 32}${voffset -5}Battery: ${font Droid Sans:style=Bold:size=8}${color1}${battery_percent BAT0}%${color}${font} ${alignr}${color2}${battery_bar 8,60 BAT0}${color}
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
${voffset -12}${goto 28}${font Arial Black:size=38}${color2}${time %H}${color}${font}${voffset -28}${font Droid Sans:style=Bold:size=11}${color2}${time :%M}${time :%S}${color}${font}
${voffset -2}${goto 100}${font Droid Sans:style=Bold:size=8}${color2}${time %A}${color}${font}
${goto 100}${time %d %b %Y}
################
# - CALENDAR - #
################
${voffset -2}${color0}${font Poky:size=15}d${font}${color}${voffset -8}${font Liberation Mono:size=8}${execpi 10800 DJS=`date +%-d`; cal | sed 's/^/${goto 32} /' | sed '1d' | sed s/" $DJS "/" "'${font Liberation Mono:style=bold:size=8}${color1}'"$DJS"'${color}${font}${font Liberation Mono:size=8}'" "/}${font}${font}${voffset -14}
####################
# - MEDIA PLAYER - #
####################
${voffset 4}${font Droid Sans:style=Bold:size=8}MEDIA PLAYER $stippled_hr${font}
${execi 6 ~/.conkycolors/bin/conkyCover}${execpi 2 ~/.conkycolors/bin/conkyBanshee -t ~/.conkycolors/templates/conkyPlayer.template}
##########
# - HD - #
##########
${voffset 4}${font Droid Sans:style=Bold:size=8}HD $stippled_hr${font}
${execpi 30 ~/.conkycolors/bin/conkyHD4}
###############
# - NETWORK - #
###############
${voffset 4}${font Droid Sans:style=Bold:size=8}NETWORK $stippled_hr${font}
# |--WLAN0
${if_up wlan0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed wlan0}${color}${font} ${alignr}${color2}${upspeedgraph wlan0 8,60 7296BB 7296BB}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totalup wlan0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed wlan0}${color}${font} ${alignr}${color2}${downspeedgraph wlan0 8,60 7296BB 7296BB}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totaldown wlan0}${color}${font}
${voffset -2}${color0}${font Poky:size=14}Y${font}${color}${goto 32} ${voffset -2}Signal: ${font Droid Sans:style=Bold:size=8}${color1}${wireless_link_qual wlan0}%${color}${font} ${alignr}${color2}${wireless_link_bar 8,60 wlan0}${color}
${voffset 4}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -8}Local IP: ${alignr}${color2}${addr wlan0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 ~/.conkycolors/bin/conkyIp}${color}
# |--ETH0
${else}${if_up eth0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed eth0}${color}${font} ${alignr}${color2}${upspeedgraph eth0 8,60 7296BB 7296BB}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totalup eth0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed eth0}${color}${font} ${alignr}${color2}${downspeedgraph eth0 8,60 7296BB 7296BB}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totaldown eth0}${color}${font}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr eth0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 ~/.conkycolors/bin/conkyIp}${color}
# |--PPP0
${else}${if_up ppp0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed ppp0}${color}${font} ${alignr}${color2}${upspeedgraph ppp0 8,60 7296BB 7296BB}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totalup ppp0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed ppp0}${color}${font} ${alignr}${color2}${downspeedgraph ppp0 8,60 7296BB 7296BB}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totaldown ppp0}${color}${font}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr ppp0}${color}
${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}${goto 32}Network Unavailable${voffset 14}${endif}${endif}${endif}
```

---

### Post by Nesh_reanimator on 2010-10-12
Same problem..

---

### Post by ninjapirate89 on 2010-10-12
Anyone have a solution or at least a reason why this would break like this?

---

### Post by sendblink23 on 2010-10-12
buu that stinks.. well for now backup those conky settings else where... forget about conky colors for a while until it gets updated... and use for now conky doing the stuff manually the old way - which is still working fine

hopefully soon enough conky colors gets fixed

---

### Post by ninjapirate89 on 2010-10-13
> **sendblink23 said:**
> buu that stinks.. well for now backup those conky settings else where... forget about conky colors for a while until it gets updated... and use for now conky doing the stuff manually the old way - which is still working fine

hopefully soon enough conky colors gets fixed

Yeah thats what I've done. I'd forgotten how much fun it is to mess around with conky manually. Here's what I whipped up after about 10 minutes in the conky thread.

[[IMG]http://i1012.photobucket.com/albums/af248/ninjapirate89/th_current_conky.png[/IMG]](http://s1012.photobucket.com/albums/af248/ninjapirate89/?action=view&current=current_conky.png)

Glad to hear it's not just me having this problem.

---

### Post by criball on 2010-10-22
I had the same problem. It seems that the cause is in the added repository:

sudo add-apt-repository ppa:norsetto/ppa

Pasting from the author's website:
"DO NOT add the above PPA or Conky Colors will not work properly!"
Removing the ppa and reinstalling conky solved the problem for me.

---

### Post by WorMzy on 2010-10-22
Does that repo upgrade conky to 1.8.1? If so, that may be the problem. I'm holding back that conky update on my Arch machine because it mangles the lower half of my conky config. It seems to be a problem specifically with conky 1.8.1.

---

### Post by Quackers on 2010-10-22
I think there was somebody on earlier who couldn't get 1.8.1 successfully compiled.

---

### Post by ninjapirate89 on 2010-10-22
I've just switched over to a handmade conky until conky-colors gets an update.

---

