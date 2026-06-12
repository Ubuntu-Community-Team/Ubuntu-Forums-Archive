---
title: "Conky Issues"
date: 2010-12-08
forum: General Help
---

### Post by helphelphelp! on 2010-12-08
Well after searching and tweaking and finally getting everything I want so far from conky I've run into some problems that i think could just be minor fixes

1) My conky won't stick to the back ground when i start up. It insist on staying over all my windows and I typically have to reopen my .conkyrc file and just resave it and the issue stops

2) the conky layout that i use has trouble using stylebats font. the capital "A" and lower case "c" symbols seems to work but not the capital "N", "T" and lower case "t". I was wondering if there was any sure fire way to fix that

3) and finally from what you can see in my picture, while the Calendar works fine, the alignment with the numbers and the days of the week are pretty off. I was wondering if there was anything wrong with the code i have that would make this happen.

here is my conky setup

```

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

#!/bin/bash
until [ "$done" = "true" ]
do
if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
then
DISPLAY=:0.0 conky -c /home/symlinked/Conky/conkymain >/dev/null 2>&1 &
#DISPLAY=:0.0 conky -c /home/symlinked/Conky/conkyclock >/dev/null 2>&1 &
#DISPLAY=:0.1 conky -c /home/symlinked/Conky/conkymain >/dev/null 2>&1 &
done="true";
else
echo "CONKY IS WAITING"
done="false"
sleep 5;
fi
done
exit 0

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent true
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 206 0
#maximum_width 220 0

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color grey
#default_shade_color black
#default_outline_color white
own_window_colour white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35
gap_y 50

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

# Network Options
if_up_strictness address

TEXT

#############
# - CLOCK - #
#############
${voffset 4}${font Pizzadude bullets:style=Bold:size=8}DATE ${hr 2}
${voffset -12}${goto 28}${font Arial Black:size=38}${color grey}${time %I}#this is where I modded it.
${color}${font}${voffset -28}${font pizzadude bullets:style=Bold:size=11}${color grey}${time :%M}${time :%S}${color}${font}
${voffset -2}${goto 100}${font pizzadude bullets:style=Bold:size=8}${color grey}${time %A}${color}${font}
${goto 100}${time %d %b %Y}

${color grey}CALENDAR ${hr 2}$color
${execpi 60 DJS=`date +%_d`; cal | sed s/"$DJS"'\b'/'${color grey}'"$DJS"'$color'/}

${font Pizzadude bullets:style=Bold:size=8}SYSTEM ${hr 2}
${voffset 4}${font StyleBats:size=9}A${font} CPU: ${cpu}% ${alignr}${cpubar 8,80}
${voffset -2}${alignr} ${alignr}${freq}MHz   ${acpitemp}°C
${voffset 0}${font StyleBats:size=9}A${font} RAM: $memperc% ${alignr}${membar 8,80}
${voffset 4}${font StyleBats:size=9}A${font} Battery: ${alignr}${battery_percent BAT1}% ${battery_time BAT1}

${font Pizzadude bullets:style=Bold:size=8}PROCESSES ${hr 2}
		${alignr}CPU%	MEM%
${voffset 2}${font PizzaDude Bullets:size=9}t${font} ${top_mem name 1}${alignr}${top_mem cpu 1}   ${top_mem mem 1}
${voffset 2}${font PizzaDude Bullets:size=9}t${font} ${top_mem name 2}${alignr}${top_mem cpu 2}   ${top_mem mem 2}
${voffset 2}${font PizzaDude Bullets:size=9}t${font} ${top_mem name 3}${alignr}${top_mem cpu 3}   ${top_mem mem 3}
${voffset 2}${font PizzaDude Bullets:size=9}t${font} ${top_mem name 4}${alignr}${top_mem cpu 4}   ${top_mem mem 4}
${voffset 2}${font PizzaDude Bullets:size=9}t${font} ${top_mem name 5}${alignr}${top_mem cpu 5}   ${top_mem mem 5}

${font Pizzadude bullets:style=Bold:size=8}STORAGE ${hr 2}
${voffset 4}${font StyleBats:size=9}c${font} ${voffset 0}Root:
	${voffset 2}${fs_used /}/${fs_size /} ${alignr}${fs_bar 8,80 /}
${voffset 4}${font StyleBats:size=9}c${font} ${voffset 0}Home:
	${voffset 2}${fs_free /home}/${fs_size /home} ${alignr}${fs_bar 8,80 /home}
${if_mounted /media/SDHC8}${voffset 2}${font StyleBats:size=9}c${font} ${voffset 0}SD Card:
	${voffset 2}${fs_used /media/SDHC8}/${fs_size /media/SDHC8} ${alignr}${fs_bar 8,80 /media/SDHC8}${endif}

${font Pizzadude bullets:style=Bold:size=8}NETWORK ${hr 2}
${if_up eth1}${voffset 2}${font PizzaDude Bullets:size=9}N${font} Upload: ${alignr}${upspeed eth1}kb/s
${voffset 2}${font PizzaDude Bullets:size=9}T${font} Download: ${alignr}${downspeed eth1}kb/s
${endif}
${if_up eth0}${voffset 2}${font PizzaDude Bullets:size=9}N${font} Upload: ${alignr}${upspeed eth0}kb/s
${voffset 2}${font PizzaDude Bullets:size=9}T${font} Download: ${alignr}${downspeed eth0}kb/s

${endif} 
```

and here is a picture of my conky

---

### Post by helphelphelp! on 2010-12-08
Bump

---

### Post by helphelphelp! on 2010-12-08
nobody knows?

---

### Post by stinkeye on 2010-12-08
1) Use a dely to start conky at boot.

2) Should work but cant tell because the config you posted doesn't show the
same result as your pic.(see my pic)

3) Use a mono or fixed width font for the calendar.eg ${font Monospace:size=8}


The conky config you posted has a bash script in it.??????????
```
#!/bin/bash
until [ "$done" = "true" ]
do
if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
then
DISPLAY=:0.0 conky -c /home/symlinked/Conky/conkymain >/dev/null 2>&1 &
#DISPLAY=:0.0 conky -c /home/symlinked/Conky/conkyclock >/dev/null 2>&1 &
#DISPLAY=:0.1 conky -c /home/symlinked/Conky/conkymain >/dev/null 2>&1 &
done="true";
else
echo "CONKY IS WAITING"
done="false"
sleep 5;
fi
done
exit 0
```
This is a script to delay conky until compiz is loaded and doesn't go in your conky.

All the info you need to configure conky can be found here.
[**_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")
[**_[COLOR="DarkRed"]Conky PitStop[/COLOR]_**]("http://conky-pitstop.wikidot.com/")

---

### Post by helphelphelp! on 2010-12-09
> **stinkeye said:**
> 1) Use a dely to start conky at boot.

2) Should work but cant tell because the config you posted doesn't show the
same result as your pic.(see my pic)

3) Use a mono or fixed width font for the calendar.eg ${font Monospace:size=8}


The conky config you posted has a bash script in it.??????????
```
#!/bin/bash
until [ "$done" = "true" ]
do
if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
then
DISPLAY=:0.0 conky -c /home/symlinked/Conky/conkymain >/dev/null 2>&1 &
#DISPLAY=:0.0 conky -c /home/symlinked/Conky/conkyclock >/dev/null 2>&1 &
#DISPLAY=:0.1 conky -c /home/symlinked/Conky/conkymain >/dev/null 2>&1 &
done="true";
else
echo "CONKY IS WAITING"
done="false"
sleep 5;
fi
done
exit 0
```
This is a script to delay conky until compiz is loaded and doesn't go in your conky.

All the info you need to configure conky can be found here.
[**_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")
[**_[COLOR="DarkRed"]Conky PitStop[/COLOR]_**]("http://conky-pitstop.wikidot.com/")

Thanks friend! I simply copied the entire code from somewhere and pasted it into my gedit.

---

### Post by stinkeye on 2010-12-09
No problem.
If you start conky in the terminal with 
```
conky -c [COLOR="Magenta"]/path/to_your/conky_config[/COLOR]
```
You can see any errors that might be in your config.

and 

if you want to use that script to delay conky at boot(Only works with compiz.)
paste into gedit and save as **.start_conky** in your home folder(the preceding dot makes it hidden...ctrl+h to show),
make executable...right click properties > permissions > allow execute.

Browse to the script in the command box in startup applications.
```
#!/bin/bash
until [ "$done" = "true" ]
do
if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
then
DISPLAY=:0.0 conky -c [COLOR="Purple"]/home/symlinked/Conky/conkymain[/COLOR] >/dev/null 2>&1 &
[COLOR="DarkOrange"]#DISPLAY=:0.0 conky -c /home/symlinked/Conky/conkyclock >/dev/null 2>&1 &
#DISPLAY=:0.1 conky -c /home/symlinked/Conky/conkymain >/dev/null 2>&1 &[/COLOR]
done="true";
else
echo "CONKY IS WAITING"
done="false"
sleep 5;
fi
done
exit 0
```
[COLOR="#800080"]Change for the path to your config.[/COLOR]
The other [COLOR="#ff8c00"]entries[/COLOR] are for starting multiple conkys but are #commented out so wont run.

---

### Post by helphelphelp! on 2010-12-09
> **stinkeye said:**
> No problem.
If you start conky in the terminal with 
```
conky -c [COLOR="Magenta"]/path/to_your/conky_config[/COLOR]
```
You can see any errors that might be in your config.

and 

if you want to use that script to delay conky at boot(Only works with compiz.)
paste into gedit and save as **.start_conky** in your home folder(the preceding dot makes it hidden...ctrl+h to show),
make executable...right click properties > permissions > allow execute.

Browse to the script in the command box in startup applications.
```
#!/bin/bash
until [ "$done" = "true" ]
do
if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
then
DISPLAY=:0.0 conky -c [COLOR="Purple"]/home/symlinked/Conky/conkymain[/COLOR] >/dev/null 2>&1 &
[COLOR="DarkOrange"]#DISPLAY=:0.0 conky -c /home/symlinked/Conky/conkyclock >/dev/null 2>&1 &
#DISPLAY=:0.1 conky -c /home/symlinked/Conky/conkymain >/dev/null 2>&1 &[/COLOR]
done="true";
else
echo "CONKY IS WAITING"
done="false"
sleep 5;
fi
done
exit 0
```
[COLOR="#800080"]Change for the path to your config.[/COLOR]
The other [COLOR="#ff8c00"]entries[/COLOR] are for starting multiple conkys but are #commented out so wont run.

Hey me again. So I got my Calendar to work and the fonts to work (i needed to download the fonts) and I'm so glad it's working... mostly

I still have the issue with it not sticking to my background. I opened my gedit, created a file called ".start_conky" saved it to my home folder, opened my home folder then right click --> properties --> permissions and had it run as an executable file. I even went as far as to go System --> Preferences --> Start Applications and ran it there but still no luck... it's just determined to open faster than any of the programs :(

---

### Post by stinkeye on 2010-12-09
Just checking.

1. right click  on **.start_conky** properties > permissions > allow execute


2. Change the path in the script from 
```
/home/symlinked/Conky/conkymain
```
to
```
/path/to_your/conky_config
```


3. Shutdown conky with (in the terminal)
```
killall conky
```

Check that the script works (compiz must be running)
```
sh .start_conky
```

4. Add to startup applications by clicking the add button and browsing to where you saved the script.

---

### Post by stinkeye on 2010-12-09
If it's still not working change this part of your conky config
```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent true
own_window_type [COLOR="#ff00ff"]override[/COLOR]
[COLOR="Magenta"]#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager[/COLOR]
```

to
```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent true
own_window_type [COLOR="#ff00ff"]normal[/COLOR]
[COLOR="#ff00ff"]own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager[/COLOR]
```

---

