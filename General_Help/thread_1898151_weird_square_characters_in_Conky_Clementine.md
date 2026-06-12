---
title: "weird square characters in Conky Clementine"
date: 2011-12-20
forum: General Help
---

### Post by shuli on 2011-12-20
I setup Conky using Conky-colors. all works and looks very well except for the clementine section showing weird square characters all over it (see screenshot attached).


conkyrc:

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
xftfont Ubuntu:size=8
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
gap_x 25
gap_y 40
minimum_size 182 600
maximum_width 182

default_bar_size 60 8

#########################
# - Graphics settings - #
#########################
draw_shades no

default_color D6D6D6

color0 F2F2F2
color1 7296BB
color2 FFFFFF

TEXT
${font Ubuntu:style=Bold:size=8}SYSTEM $stippled_hr${font}
##############
# - SYSTEM - #
##############
${color0}${voffset 6}${font OpenLogos:size=19}u${font}${color}${goto 32}${voffset -14}Kernel:  ${alignr}${color2}${kernel}${color}
${goto 32}uptime: ${alignr}${color2}${uptime}${color}
# |--CPU
${offset 2}${color0}${font Poky:size=16}P${color}${font}${voffset -4}${goto 32}CPU: ${font Ubuntu:style=Bold:size=8}${color1}${cpu cpu1}%${color}${font} ${alignr}${color2}${cpugraph cpu1 8,60 7296BB 7296BB}${color}
# |--MEM
${color0}${font Poky:size=16}M${font}${color}${goto 32}${voffset -7}RAM: ${font Ubuntu:style=Bold:size=8}${color1}$memperc%${color}${font}
${offset 1}${voffset 2}${color0}${membar 4,18}${color}${goto 32}${voffset -2}F: ${font Ubuntu:style=Bold:size=8}${color2}${memeasyfree}${color}${font} U: ${font Ubuntu:style=Bold:size=8}${color2}${mem}${color}${font}
#############
# - CLOCK - #
#############
${voffset 4}${font Ubuntu:style=Bold:size=8}DATE $stippled_hr${font}
${voffset -10}${alignc 46}${color2}${font Arial Black:size=30}${time %H:%M}${font}${color}
${alignc}${time %d %B %Y}
####################
# - MEDIA PLAYER - #
####################
${voffset 4}${font Ubuntu:style=Bold:size=8}MEDIA PLAYER $stippled_hr${font}
${execpi 2 /usr/share/conkycolors/bin/conkyClementine -t /home/shuli/.conkycolors/templates/conkyPlayer.template}
```

conkyclementine template:

```
${if_running clementine}
${voffset -12}${color0}${font Musicelements:size=18}z${font}${color}${voffset -8}${goto 32}Status:${alignr}${color2}[--datatype=ST]${color}
${voffset 4}${goto 32}${color2}[--datatype=AR]${color}
${color2}${goto 32}[--datatype=AL]${color}
${color2}${goto 32}[--datatype=TI]${color}
${voffset 4}${goto 32}${color2}[--datatype=PT]/[--datatype=LE]${color}${alignr}${color2}${execbar /usr/share/conkycolors/bin/conkyClementine --datatype=PP}${color}$else
${voffset -12}${color0}${font Webdings:size=16}U${font}${color}${voffset -2}${goto 32}Status:${alignr}${color2}off${color}
${voffset 12}$alignc${font Droid Sans:style=Bold:size=8}${color2}Clementine${color}${font}${voffset -10}
$endif
```

Anyone else have this issue/solution?

---

### Post by DogMatix on 2011-12-20
It could be a font issue. Missing characters often show as a oblong box

---

### Post by lechien73 on 2011-12-20
It looks like a font problem...do you have the listed fonts: Musicelements, Droid sans, and Webdings installed?

I also saw that people were experiencing those square characters when the config file had been edited in Windows, which added unrecognized newline characters to the end each line.

---

### Post by shuli on 2011-12-20
do you know a quick way to get a listing of all fonts installed?

These files were not edited on a windows machine. They were created on this machine using conky-colors.

---

### Post by lechien73 on 2011-12-20
Just open a terminal window and type:

```
fc-list | more
```

---

### Post by shuli on 2011-12-20
all fonts seem to be installed.

---

### Post by shuli on 2011-12-20
I made a little progress on this. I was messing around with the template file and by adding some empty rows like this:
```
${if_running clementine}
${voffset -12}${color0}${font Musicelements:size=18}z${font}${color}${voffset -8}${goto 32}Status:${alignr}${color2}[--datatype=ST]${color}

${voffset 4}${goto 32}${color2}[--datatype=AR]${color}

${color2}${goto 32}[--datatype=AL]${color}

${color2}${goto 32}[--datatype=TI]${color}

${voffset 4}${goto 32}${color2}[--datatype=PT]/[--datatype=LE]${color}${alignr}${color2}${execbar /usr/share/conkycolors/bin/conkyClementine --datatype=PP}${color}$else
${voffset -12}${color0}${font Webdings:size=16}U${font}${color}${voffset -2}${goto 32}Status:${alignr}${color2}off${color}
${voffset 12}$alignc${font Droid Sans:style=Bold:size=8}${color2}Clementine${color}${font}${voffset -10}
$endif
```
I managed to get rid of the squares but now i have these huge spaces between the lines (see image attached)
how would i go about reducing those spaces between the lines?

---

