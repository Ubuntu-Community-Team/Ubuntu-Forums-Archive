---
title: "Multi conky doesn't starts"
date: 2009-12-05
forum: General Help
---

### Post by sowhat123456789a on 2009-12-05
I can't start two conkys with two different conkyrc files with this code : 

conky & conky -c -/.conkyrc2

On this code "-" is an character which I can not write on this forum.
(to see the character please look at the search string [http://www.google.com/search?source=hp&q=~&um=1&ie=UTF-8&sa=N&hl=tr&tab=iw](http://www.google.com/search?source=hp&q=~&um=1&ie=UTF-8&sa=N&hl=tr&tab=iw) )

---

### Post by stinkeye on 2009-12-05
Here's an example of a script to toggle your conkys on and off.
Adjust for your needs, make executable and create a shortcut in your panel.
```
#!/bin/sh

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
sleep 1 &&
 exec conky -c ~/conky/conkypanel &
sleep 3 &&
 exec conky -c ~/conky/conkycal &
sleep 3 &&
 exec conky -c ~/conky/conkyclocklua2 &
sleep 4 &&
 exec conky -c ~/conky/conkyplaytime &
sleep 5 &&
 exec conky -c ~/conky/conkysb &
sleep 6 &&
 exec conky -c ~/conky/conkysro &
sleep 7 &&
 exec conky -c ~/conky/conkytide &
sleep 9 &&
 exec conky -c ~/conky/rottoswellmini &
sleep 10 &&
 exec conky -c ~/conky/conkygmail &
fi
```
eg
```
#!/bin/sh

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
sleep 1 &&
 exec conky &
sleep 3 &&
 exec conky -c ~/.conkyrc2 &

fi
```
I can write "~".

[_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_]("http://ubuntuforums.org/showpost.php?p=5436679&postcount=1")

---

### Post by sowhat123456789a on 2009-12-05
Thank you but I didn't understand exactly what you mean...

I have two conkyrc files :

~/.conkyrc
~/.conkyrc2

I want to add both of them to startup programs. I want to know which is the command I need ? 
I tried :

conky & conky -c ~/.conkyrc2

But it doesn't work. (but I remember that before I format Ubuntu it worked for me). I don't need a shortcut on my desktop but just a command for startup programs.
They are starting (I can see them after I neter my password for a few seconds) but they are dissepear when my gnome desktop is exactly ready.

Thanks!

---

### Post by stinkeye on 2009-12-05
What I gave you was an easy way to stop/start conky when your configuring conky.
If you want autostart copy this```
#!/bin/bash
sleep 17 &&	# 0 good for Xfce - use 20 to 30 for Gnome
 conky -c ~/.conkyrc &
sleep 18 &&
 conky -c ~/.conkyrc2 &
  
```
***Check that .conkyrc and .conkyrc2 are in your home folder.
Save the script in your home folder as .startconky
Right click on that file(ctrl+h to show hidden) ...properties > permissions
and tick the execute box.
In startup applications link to .startconky by clicking the browse button.
You may have to hit ctrl+h to see it.
On gnome it's best to delay the start of conky so it loads after the window manager.

If that doesn't work post your conky config.
It could be as simple as changing *own_window_type override* to *own_window_type normal* in your config.
Are you using compiz?

---

### Post by sowhat123456789a on 2009-12-06
Yes I use compiz.

I create afile .starconky:

#!/bin/bash
sleep 30 &&
 conky -c ~/.conkyrc &
sleep 30 &&
 conky -c ~/.conkyrc2 &

and after that I set it as executable file. And I add this file to startup manager. But conky didn't start. (and what does sleep 30 means ? )

/.conkyrc2
```
font Sans:size=8
use_xft yes
update_interval 3
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 900
maximum_width 900
default_color white
alignment top_right
gap_x 200
gap_y 80
cpu_avg_samples 2
override_utf8_locale no
uppercase yes

TEXT
${exec lsof -i}
```

/.conkyrc
```
font Sans:size=8
use_xft yes
update_interval 1
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 220
maximum_width 220
default_color white
alignment top_left
gap_x 20
gap_y 50
cpu_avg_samples 2
override_utf8_locale no
uppercase yes

TEXT
Uptime: $alignr$uptime

Processes: ${alignr}$processes ($running_processes running)

CPU1 ${alignr}${cpu cpu1}%
${cpubar 4 cpu1}

CPU2 ${alignr}${cpu cpu2}%
${cpubar 4 cpu2}

CPU3 ${alignr}${cpu cpu3}%
${cpubar 4 cpu3}

CPU4 ${alignr}${cpu cpu4}%
${cpubar 4 cpu4}

Ram ${alignr}$mem / $memmax ($memperc%)
${membar 4}

swap ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Highest CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}
${top name 4}$alignr${top cpu 4}${top mem 4}

Highest MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}
${top_mem name 4}$alignr${top_mem cpu 4}${top_mem mem 4}

Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107} ${alignr}${upspeedgraph eth0 25,107}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

HDD WRITE $alignr $diskio_write
${diskiograph_write }
HDD READ $alignr $diskio_read
${diskiograph_read }

CPU FAN${alignr}${exec sensors | grep "fan1:" | cut -c13-16 ;} PRM
HDD$alignr${hddtemp /dev/sda 0.0.0.0 7634}
MOTHERBOARD $alignr ${hwmon temp 1}C
CPU 1${alignr}${exec sensors | grep "Core 0:" | cut -c13-16 ;}
CPU 2${alignr}${exec sensors | grep "Core 1:" | cut -c13-16 ;}
CPU 3${alignr}${exec sensors | grep "Core 2:" | cut -c13-16 ;}
CPU 4${alignr}${exec sensors | grep "Core 3:" | cut -c13-16 ;}

```

If I start them from the terminal they are opening properly.

Thanks!

---

### Post by stinkeye on 2009-12-06
sleep - delay for a specified amount of time.
If you click on the .startconky file and choose run does it work.
You'll have to wait 30 secs.
Also In my conky config I use *own_window_type normal* not *own_window_type override*

---

### Post by stinkeye on 2009-12-06
OK, I just did a bit of testing and your conkys will display on my system
but it appears that using the "~" symbol for your home folder doesn't work
from within startup applications.
So you could probably go back to using your original one but use the full path
eg /home/[COLOR="Sienna"]your-username[/COLOR]/ instead of "~"
But if your using compiz I recommend using a delay script.

This is what I use.It will not start conky until compiz is fully loaded
```
#! /bin/bash
until [ "$done" = "true" ]
do
	if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
	then
		DISPLAY=:0.0 conky -c [COLOR="#8b0000"]~/path-to-conkyrc[/COLOR] >/dev/null 2>&1 &
                sleep 2;
                DISPLAY=:0.0 conky -c [COLOR="DarkRed"]~/path-to-conkyrc2[/COLOR] >/dev/null 2>&1 &
               
                
		done="true";
	else
		echo "CONKY IS WAITING"
		done="false"
		sleep 5;
	fi
done
exit 0
```
[COLOR="#8b0000"]Change for the location of your conkys[/COLOR]
Same as before, save in home as whatever you like and make executable.
Link to it in startup applications using the browse button so you get the full path.
[COLOR="DarkOrange"][SIZE="5"]For this script to work you must have the Dbus plugin enabled.[/SIZE][/COLOR]
It is under utilities in CCSM.

---

### Post by sowhat123456789a on 2009-12-06
stinkeye thank you! problem solved... Conky starts now :)

My conky is stinky on desktop. I can't move it by pressing on "show desktop" button. That's good. But I have another problem. Some of desktop icons are back on conky. So I can't see them. First I have to kill conky process and then, start conky again. Now you can tell me to disable the option "stinky desktop", but i remember that there is a solution for that...

---

### Post by stinkeye on 2009-12-06
> **sowhat123456789a said:**
> stinkeye thank you! problem solved... Conky starts now :)

My conky is stinky on desktop. I can't move it by pressing on "show desktop" button. That's good. But I have another problem. Some of desktop icons are back on conky. So I can't see them. First I have to kill conky process and then, start conky again. Now you can tell me to disable the option "stinky desktop", but i remember that there is a solution for that...
Conky will cover desktop icons if it has focus eg you click on it.
Solution move conky to the right hand side using these variables to change
its position
```
alignment top_left
gap_x 20
gap_y 50
```
eg change ```
alignment top_right
```
enter ```
man conky
```
in terminal for info.
P.S I liked the Freudian slip, calling your conky stinky instead of sticky.I reall appreciate you naming your conky after me.:p;)
To not have your conky stick to all desktops change *own_window_type override* to *own_window_type normal* because override does just that.
It overrides own_window_hints and defaults to sticky.
Now just delete the sticky variable from own_window_hints undecorated,below,[COLOR="DarkRed"]sticky[/COLOR],skip_taskbar,skip_pager

If your conky minimizes when you "show desktop" goto 
compizconfig settings manager > general options 
and untick *hide skip taskbar windows*

**Please mark as solved in thread tools(top right)**

---

### Post by sowhat123456789a on 2009-12-06
Thank you stinkeye ! :D

---

### Post by stinkeye on 2009-12-06
No problem.

---

