---
title: "Conky startup"
date: 2010-02-23
forum: General Help
---

### Post by cinger on 2010-02-23
I'm running on karmic 9.10, gnome, got conky working great, even local weather, but having problems with autostartup.

at terminal, commands conky or /usr/bin/conky work to start conky with no problem.  tried adding it to startup applications, and conky displays (with correct time) just after login, but then desktop wallpaper covers it completely (it doesn't do this from when started from the terminal).  At logout, conky flashes briefly (with correct time) immediately before logout.  

after login in autostarted conky, system monitor says conky is sleeping; the Waiting Channel displays "poll_channel_timeout" (forever).  However, when conky is initiated from the terminal, Waiting Channel will cycle through "poll_schedule_timeout", then "pipe_wait".

background is set to yes in .conkyrc, so I can close terminal and conky keeps running.

I tried to change the autostart file to a bash file that first sleeps and then runs conky, but still no luck, right after login conky starts (with correct time) but then the desktop wallpaper covers it.  I've gone up to sleep 200.  This is the bash script that I modified from another website about autostarting conky.  Let me know if I should provide any other information.

> #!/bin/bash
sleep 200 &&   # 0 good for Xfce - use 20 to 30 for gnome
conky
#sleep 0 &&
#conky

---

### Post by stinkeye on 2010-02-23
Post your conky config and are you using compiz.

---

### Post by cinger on 2010-02-23
Think I may have gotten it.

changed own_window_type from override to normal.

tried changing just about every other setting in own_window block.


Here is my .conkyrc

```
#!/bin/bash
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
#

#Run in background
background yes

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 3.0
 
# Minimum size of text area
# minimum_size 250 5
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
 
# Stippled borders?
stippled_borders 3
 
# border margins
border_margin 9
 
# border width
border_width 10
 
# Default colors and also border colors, grey90 == #e5e5e5
default_color grey
 
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
 
# stuff after 'TEXT' will be formatted on screen
 
TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine
 
${color orange}Date & Time ${hr 2}${color}
${alignc}${font Arial Black:size:24}${time %H:%M}${font}
${alignc}${Time %A  %m . %d . %Y}

${execpi 300 cal | sed -e 's/'`date | awk '{print $3}'`'/\$\{color e84448}'`date | awk '{print $3}'`'\$\{color}/'|sed 's/^/${alignr}/'}

${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
 
${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color
 
Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color
hda1:  ${fs_free_perc /media/sda1}%   ${fs_bar 6 /media/sda1}$color
 
${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}
 
${color orange} WEATHER ${hr 2}${color}
${execi 1800 /home/colin/weather/nwsweather.sh}

```

---

### Post by stinkeye on 2010-02-23
So it starts ok on login?
These are the settings I use in my conky
```
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,sticky,below,skip_taskbar,skip_pager
```
If your using compiz I have a startup script that will delay the start of conky until compiz has loaded.

---

### Post by IAmNoodle on 2010-02-23
> **stinkeye said:**
> So it starts ok on login?
These are the settings I use in my conky
```
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,sticky,below,skip_taskbar,skip_pager
```
**If your using compiz I have a startup script that will delay the start of conky until compiz has loaded.**

That would be quite useful for myself actually if you wouldn't mind posting it. I've been having exactly the same problem as the thread starter

---

### Post by stinkeye on 2010-02-23
Does your calendar line up properly.
Looks like this on mine.
[ATTACH]148051[/ATTACH]

For calendars you should use a mono font.

Try changing this line in your conky
```
${execpi 300 cal | sed -e 's/'`date | awk '{print $3}'`'/\$\{color e84448}'`date | awk '{print $3}'`'\$\{color}/'|sed 's/^/${alignr}/'}
```
to
```
${font LCDMono:bold:size=8}${execpi 300 cal | sed -e 's/'`date | awk '{print $3}'`'/\$\{color e84448}'`date | awk '{print $3}'`'\$\{color}/'|sed 's/^/${alignc}/'}${font}
```
[ATTACH]148052[/ATTACH]

[_**[COLOR="DarkRed"]http://www.dafont.com/lcd-lcd-mono.font[/COLOR]**_]("http://www.dafont.com/lcd-lcd-mono.font")
Place the font in /home/[COLOR="Navy"]your_username[/COLOR]/.fonts
dot files and folders are hidden. ctrl + h to show hidden.
If you don't have a .fonts folder , create one.

---

### Post by stinkeye on 2010-02-23
> **IAmNoodle said:**
> That would be quite useful for myself actually if you wouldn't mind posting it. I've been having exactly the same problem as the thread starter

This is what I use.It will not start conky until compiz is fully loaded
```
#! /bin/bash
until [ "$done" = "true" ]
do
	if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
	then
		DISPLAY=:0.0 conky -c [COLOR="Red"]~/path-to-conkyrc[/COLOR] >/dev/null 2>&1 &
                
               
		done="true";
	else
		echo "CONKY IS WAITING"
		done="false"
		sleep 5;
	fi
done
exit 0
```
[COLOR="#ff0000"]Change for the location of your conky[/COLOR]
Save in home as whatever you like and make executable.
Link to it in startup applications using the browse button so you get the full path.
**[COLOR="#ff0000"]For this script to work you must have the Dbus plugin enabled.[/COLOR]**
It is under utilities in CCSM.

If your using more than one conky just add your other conky 
eg I start 7 conkys
```
#! /bin/bash
until [ "$done" = "true" ]
do
	if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
	then
		DISPLAY=:0.0 conky -c ~/conky/conkypanel >/dev/null 2>&1 &
                #sleep 2;
                #DISPLAY=:0.0 conky -c ~/conky/conkytide >/dev/null 2>&1 &
                sleep 3;
                #DISPLAY=:0.0 conky -c ~/conky/conkyclocklua2 >/dev/null 2>&1 &
		DISPLAY=:0.0 conky -c ~/conky/conkycal >/dev/null 2>&1 &
                sleep 5;
                DISPLAY=:0.0 conky -c ~/conky/conkysro >/dev/null 2>&1 &
                DISPLAY=:0.0 conky -c ~/conky/conkysb >/dev/null 2>&1 &
                DISPLAY=:0.0 conky -c ~/conky/conkyplaytime >/dev/null 2>&1 &
                sleep 6;
                DISPLAY=:0.0 conky -c ~/conky/conkygmail >/dev/null 2>&1 &
                DISPLAY=:0.0 conky -c ~/conky/rottoswellmini >/dev/null 2>&1 &
                
		done="true";
	else
		echo "CONKY IS WAITING"
		done="false"
		sleep 5;
	fi
done
exit 0
```

---

### Post by cinger on 2010-02-24
I think the problem was my startup application setup.  I originally set the startup app to /usr/bin/conky which didn't work.  Then I read that in gnome I should to change the startup app to a bash file .startconky that first sleeps 30 and then exec conky.  I tried to just overwrite the original startup application /usr/bin/conky and then found out that it wasn't saved properly (after adjusting almost every other parameter in .conkyrc.  When I figured that out I wrote a new startup application to /home/user/.startconky, adjusted .conkyrc to background no (default) and it works fine.  

Thanks for the calendar tip, btw.  spent a long time messing with that.

---

