---
title: "Why Is My Conky Staying Above All Windows?"
date: 2012-07-25
forum: General Help
---

### Post by wpwend42 on 2012-07-25
My Conky is suddenly staying above all windows. I'm not sure what needs to be changed here, but if someone could point me in the right direction I would appreciate it. I miss going to the desktop and seeing my conky =(

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,skip_taskbar, skip_pager
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
# fiddle with window
use_spacer yes
use_xft yes
# Update interval in seconds
update_interval 1.0
# Minimum size of text area
minimum_size 180 0
# Draw shades?
draw_shades yes
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
# Stippled borders?
stippled_borders 8
# border margins
border_margin 4
# border width
border_width 1
# minimum size
minimum_size 0 780
# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white
own_window_colour brown
own_window_transparent yes
# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
# Gap between borders of screen and text
gap_x 10
gap_y 10
override_utf8_locale yes
xftfont Terminus:size=8
xftalpha 0.8
short_units on
# stuff after 'TEXT' will be formatted on screen
TEXT
DATE ${hr 2}
${alignc 60}${font Arial Black:size=26}${time %H:%M:%S}${font}
${alignc}${time %A %d %B %Y}
${execpi 60 DJS=`date +%_d`; cal -h| sed s/"\(^\|[^0-9]\)$DJS"'\b'/'\1${color orange}'"$DJS"'$color'/}
${head /home/william/gcal.txt 20 20}
DISKS ${hr 2}
HOME: ${fs_free /home}/${fs_size /home}${alignr}${fs_bar 10,120 /home}
NOW PLAYING ${hr 2}
${alignc}${exec conkyBanshee --datatype=AR}
${alignc}${exec conkyBanshee --datatype=TI}
${alignc}${exec conkyBanshee --datatype=AL} (${exec conkyBanshee --datatype=YR})
${alignc}${exec conkyBanshee --datatype=PT} / ${alignc}${exec conkyBanshee --datatype=LE}
SYSTEM ${hr 2}
${voffset 2}${font OpenLogos:size=16}u${font} Kernel: ${alignr}${kernel}
${font StyleBats:size=16}q${font} Uptime: ${alignr}${uptime}
${font StyleBats:size=16}A${font} CPU1: ${freq_g cpu1} GHz ${cpu cpu1}% ${alignr}${cpugraph cpu1 20,120 000000 ff0000}
${font StyleBats:size=16}A${font} CPU2: ${freq_g cpu2} GHz ${cpu cpu2}% ${alignr}${cpugraph cpu2 20,120 000000 00ff00}
HIGHEST CPU ${hr 2}
${color #ddaa00} ${top name 1}${top_mem cpu 1}
${color lightgrey} ${top name 2}${top cpu 2}
${color lightgrey} ${top name 3}${top cpu 3}
HIGHEST MEM ${hr 2}
${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${color lightgrey} ${top_mem name 3}${top_mem mem 3}

---

### Post by ajgreeny on 2012-07-25
Line 4:  try** "own_window_type normal**"

That's the only real difference I can see between yours and mine that might  account for your window being on top all the time

---

### Post by HiImTye on 2012-07-25
I used to use override but changed it to normal for this exact reason in 11.10. just change it to normal and it should work fine.

---

### Post by BoogeyOfTheMan on 2012-07-25
Mine is set to override and it works fine...ish. (Sometimes the transperancy turns a milky white or disappears altogether) But it always stays behind everything as long as it was the last thing to be loaded on boot.

Try:```

killall conky
conky

```

---

### Post by HiImTye on 2012-07-25
right, you do need to wait for the WM to load before loading conky. it was other issues that caused me to change to normal.

simply add a delay to whatever command you use to load conky at boot such as:


sleep 25; conky -c/home/myname/conky/conky.cfg

edit: you could also use something like in my conky setup: [http://ubuntuforums.org/showthread.php?t=1960742](http://ubuntuforums.org/showthread.php?t=1960742)

---

### Post by wpwend42 on 2012-07-25
Hey, setting it to normal worked! Thanks.

Mine does that Milky white in both Ubuntu 12.4 and Linux Mint 12...maybe once every few weeks. If I kill it in the terminal and restart, it goes away.

---

### Post by BoogeyOfTheMan on 2012-07-26
Are you using a lua script for a semi transparent background?

---

