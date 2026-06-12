---
title: "Conky help"
date: 2010-08-31
forum: General Help
---

### Post by polardude1983 on 2010-08-31
Ok so i have done a $voffset 210 for a twitter script that I am calling but only the first tweet is indented 210, the rest is unindented

MY CONKY

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

#####################
# - Text settings - #
#####################
use_xft yes
xftfont Droid Sans:size=8
override_utf8_locale yes
text_buffer_size 10000

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
gap_y 69

minimum_size 1000 576
maximum_width 500


default_bar_size 60 8

#########################
# - Graphics settings - #
#########################
draw_shades no

default_color 000000

color0 black
color1 E07A1F
color2 black
color5 994c00
color6 000064

lua_load ~/scripts/photo_album.lua
lua_draw_hook_pre photo_album

TEXT
##HI##
${offset 414}${color6}${font angelina:size=12}${execi 1680 python /home/christoph/scripts/conkyForecast.py --location=USTX0482 --datatype=CN --refetch}
${offset 385}${color6}Today:${offset 4}${color2}${execi 1680 python /home/christoph/scripts/conkyForecast.py --location=USTX0482 --datatype=CT}
${offset 300}${voffset -34}${color6}${font Weather:size=74}${execi 1680 python /home/christoph/scripts/conkyForecast.py --location=USTX0482 --datatype=WF}${font}
${offset 390}${voffset -48}${color6}${font angelina:size=12}Temperature: ${color0}${font daniel:size=8}${execi 1680 python /home/christoph/scripts/conkyForecast.py --location=USTX0482 --datatype=HT}
${offset 400}${voffset 2}${color6}${font angelina:size=12}Windspeed: ${color0}${execi 1680 python /home/christoph/scripts/conkyForecast.py --location=USTX0482 --datatype=WS}
${offset 418}${voffset 2}${color6}${font angelina:size=12}Humidity: ${color0}${execi 1680 python /home/christoph/scripts/conkyForecast.py --location=USTX0482 --datatype=HM}

##HI##
${offset 320}${font Droid Sans:style=Bold:size=8}SYSTEM ${font}
##############
# - SYSTEM - #
##############
${offset 320}${color0}${font Poky:size=15}S${font}${color}${goto 32}${offset 320}${voffset -8}Kernel:  ${alignr}${color2}${kernel}${color}
${goto 32}${offset 320}Uptime: ${alignr}${color2}${uptime}${color}
# |--CPU
${offset 320}${color0}${font Poky:size=16}P${color}${font}${voffset -4}${goto 32}${offset 320}CPU: ${font Droid Sans:style=Bold:size=8}${color1}${cpu cpu1}%${color}${font} ${alignr}${color2}${cpugraph cpu1 8,60 CE5C00 E07A1F}${color}
# |--MEM
${offset 320}${color0}${font Poky:size=16}M${font}${color}${goto 32}${voffset -7}${offset 320}RAM: ${font Droid Sans:style=Bold:size=8}${color1}$memperc%${color}${font}
${voffset 10}${offset 320}${color0}ROOT:    ${color }${fs_free /}/${fs_size /}
${voffset 7}${offset 320}${color0}HOME:  ${color0}${fs_free /home}/${fs_size /home}
${voffset 7}${offset 320}${color0}Backup:  ${color0}${fs_free /media/Backup__}/${fs_size /media/Backup__}
${voffset 65}${offset 316}${color5}${font christopherhand:size=21}${texeci 60 perl ~/scripts/gmail.pl n} ${color5}Unread Emails (Inbox)${color}${font times:size=8}${voffset 8}
${offset 330}${execi 60 perl ~/scripts/gmail.pl s}

#############
# - CLOCK - #
#############
##${voffset 208}${offset 192}${font arial:size=8}${rss http://www.feed43.com/6153216347707372.xml 1 item_titles 10 | fold -w59}##
##${font Sans:size=10}${execi 120 /home/christoph/scripts/twittersearch polardude1983 | head -n 5}##
${offset 192}${font arial:size=6.5}${voffset 200}${execi 60 python /home/christoph/scripts/cwitter.py | fold -w79}


${voffset 20}${font denne at the tea party:size=20}${color6}${offset 320}${alignc}${time %B %y}
${voffset 1}${font Arenski:size=12}${color6}${offset 310}${alignc}${time %A %d %Y}



```

My desktop and what it looks like so you can see

[IMG]http://i.imgur.com/NrYla.jpg

---

### Post by VCoolio on 2010-08-31
There is a way of course, but I forgot. For now you could just create a new conky config for the twitter thing that you align completely to the right coordinates. You can call several configs using for example "conky -c /folder/config1 && conky -c /folder/config2".

---

### Post by inso_741 on 2010-08-31
as far as I know voffset is for vertical alignment....is it not?

---

### Post by mobilediesel on 2010-08-31
> **polardude1983 said:**
> Ok so i have done a $voffset 210 for a twitter script that I am calling but only the first tweet is indented 210, the rest is unindented

MY CONKY


My desktop and what it looks like so you can see

[IMG]http://i.imgur.com/NrYla.jpg

The part that is actually doing the indent is the **${offset 192}**
So change this line:
```
${offset 192}${font arial:size=6.5}${voffset 200}${execi 60 python /home/christoph/scripts/cwitter.py | fold -w79}
```
to this:
```
${font arial:size=6.5}${voffset 200}${execpi 60 python /home/christoph/scripts/cwitter.py | fold -w79 | sed 's/^/${offset 192}/'}
```
and it will indent every line output by your script.

---

### Post by polardude1983 on 2010-08-31
Thank you also is there a way to wrap text in conky from an rss feed?

```
${voffset 205}${font arial:size=8}${rss http://www.feed43.com/6153216347707372.xml 1 item_titles 10 | fold -w59}
```

I tried the fold -w59 but that is not wrapping it. It's still cutting off the titles if they are 2 long.

---

### Post by polardude1983 on 2010-08-31
OK so i figured how to wrap it if i did it in a sh script.

```
${execi 300 /home/christoph/scripts/conky-rss.sh | fold -w66}
```

I'm sure i will have more Q's

---

