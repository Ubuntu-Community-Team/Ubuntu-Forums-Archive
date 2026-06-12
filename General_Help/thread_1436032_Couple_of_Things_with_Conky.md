---
title: "Couple of Things with Conky"
date: 2010-03-22
forum: General Help
---

### Post by asdf-laptop on 2010-03-22
Alright, I recently installed Linux (Ubuntu 9.10). I'm totally new to Linux and wasn't really savvy with Windows either, so bear with me. 

After installing, I decided my first objective would be to customize my desktop, which made me come across Conky. So far I've set up the Weather script and added a space for me to write reminders. Now, I'm trying to install the Pidgin script, but I definitely don't have enough room in my Conky panel (I have a lot of contacts). Also, I don't like the format of it and can't figure out how to not make it double spaced between usernames (it's double spaced to show status messages under a person's username--I dont care for that). 

So, I need to make a new Conky panel (i'd like it side by side the original) with Pidgin on it. And for the Pidgin format to not be double spaced for status messages. Basically I just need a simple list of all current people online. 

Note: I tried to google how to have multiple Conkys and came across the solution of making two configs and then typing:

conky -c conkyrc1
conky -c conkyrc2

I got a bunch of errors when trying to execute the second config file. I basically copied the first config file and renamed it + changed the position to top_middle instead of top_left (this is just an example of how noobie I am). 

Sorry for being such a noob, but I do wish to learn!

Attached a picture of my current Conky panel and here's my current .conkyrc:

```

use_xft yes
xftfont Liberation Sans:size=8
override_utf8_locale yes

text_buffer_size 2048
update_interval 1
total_run_times 0
double_buffer yes
no_buffers yes
net_avg_samples 1
cpu_avg_samples 1

own_window_class Conky
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

default_color cccccc
draw_shades no

color0 white
color1 E07A1F
color2 white

alignment top_left
gap_x 25
gap_y 40
minimum_size 182 0
maximum_width 182

default_bar_size 60 8

imlib_cache_size 0

TEXT
${font Liberation Sans:style=Bold:size=8}SYSTEM $stippled_hr${font}
${color0}${font Poky:size=15}S${font}${color}${goto 32}${voffset -8}Kernel:  ${alignr}${color2}${kernel}${color}
${goto 32}Uptime: ${alignr}${color2}${uptime}${color}
# --CPU
${offset 1}${color0}${font Poky:size=16}P${font}${offset -19}${voffset 9}${cpubar cpu0 4,18}${color}${voffset -16}${goto 32}CPU1: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu1}%${color}${font} ${alignr}${color2}${cpugraph cpu1 8,60 CE5C00 E07A1F}${color}
${goto 32}CPU2: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu2}%${color}${font} ${alignr}${color2}${cpugraph cpu2 8,60 CE5C00 E07A1F}${color}
# --MEM
${color0}${font Poky:size=16}M${font}${color}${goto 32}${voffset -7}RAM: ${font Liberation Sans:style=Bold:size=8}${color1}$memperc%${color}${font}
${offset 1}${voffset 2}${color2}${membar 4,18}${color}${goto 32}${voffset -2}F: ${color2}${memeasyfree}${color} U: ${color2}${mem}${color}
# --HD
${voffset -2}${color0}${font Poky:size=15}y${font}${color}${offset 6}${voffset -7}Root: ${font Liberation Sans:style=Bold:size=8}${color1}${fs_free_perc /}%${color}${font}
${voffset 2}${color0}${fs_bar 4,20 /}${color}${offset 8}${voffset -2}F:${color2}${fs_free /}${color} U:${color2}${fs_used /}${color}
# CLOCK
${voffset 4}${font Liberation Sans:style=Bold:size=8}DATE $stippled_hr${font}
${voffset -10}${alignc 46}${color2}${font Arial Black:size=30}${time %H:%M}${font}${color}
${alignc}${time %d %B %Y}
# WEATHER
${offset -5}${color3}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=11}Weather${font}  ${hr}${color1}
${execpi 1800 conkyForecast --location=USIL0225 --template=/home/asdf/.conkycolors/templates/conkyForecast.template}
# Notes
${font Liberation Sans:style=Bold:size=8}NOTES (gedit .conkyrc) $stippled_hr${font} 
ASTROPHYS LAB 2/16 
ASTROBIO PRE 2/17 
ANALYSIS SHEET 2/17 
ANALYSIS TEST 2/17
GAME THEORY TEST 2/18
# Pidgin
${color4}${font Terminus:style=Bold:size=14}@ ${font Terminus:style=Bold:size=11}Pidgin${font}

${color4}Template Output:
${color1}${execpi 60 conkyPidgin -t /usr/share/conkypidgin/example/conkyPidgin.template -C ^ -A a -U x -N s -W P -M ~ -F r}

${color4}Standard Output:
${voffset 5}${color1}${font}${execi 60 conkyPidgin
```

---

### Post by Ildanach on 2010-05-13
That's a nice setup. I've been experimenting with conky too, but haven't come across having pidgin in it. 

Anyways, you may have already seen this, but i'm trying something similar, and came across [this]("http://crunchbanglinux.org/wiki/howto/howto_setup_multiple_conky_sessions") website. Hope it helps!

---

### Post by 2hot6ft2 on 2010-05-14
You didn't provide the conkyPidgin.template for anyone to tell you how to fix what you're wanting. And your conkyrc was cut short since it didn't end with a }

Here are some useful threads and other info..

Beginners guide to conky (a little dated but still good info.)
[http://ubuntuforums.org/showthread.php?t=867076](http://ubuntuforums.org/showthread.php?t=867076)

Conky weather forcast (don't overlook this one it guides you thru setting up the PPA, and better images like in the attached pic.)
[http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328)

Conky files and screenshots
[http://ubuntuforums.org/showthread.php?p=8713982](http://ubuntuforums.org/showthread.php?p=8713982)

Conky GUI
[http://conkygui.sourceforge.net/](http://conkygui.sourceforge.net/)
[http://sourceforge.net/projects/conkygui/files/](http://sourceforge.net/projects/conkygui/files/)

Conky Hardcore
[http://conky.linux-hardcore.com/?page_id=144](http://conky.linux-hardcore.com/?page_id=144)
[http://www.linux-hardcore.com/forum/index.php?PHPSESSID=ea2ab48a2e01a51544ac45cdcd65d21b&board=80.0](http://www.linux-hardcore.com/forum/index.php?PHPSESSID=ea2ab48a2e01a51544ac45cdcd65d21b&board=80.0)
[http://conky.linux-hardcore.com/?page_id=851](http://conky.linux-hardcore.com/?page_id=851)

Conky Astronomy pic. of the day
[http://maktfri.wordpress.com/2010/01/27/get-astronomy-picture-of-the-day-in-conky/](http://maktfri.wordpress.com/2010/01/27/get-astronomy-picture-of-the-day-in-conky/)

Have fun
:guitar:

---

