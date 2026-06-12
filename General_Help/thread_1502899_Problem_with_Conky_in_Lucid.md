---
title: "Problem with Conky in Lucid"
date: 2010-06-06
forum: General Help
---

### Post by primolarry on 2010-06-06
Hi there,

I've been using conky for some time now, and I haven't changed conkyrc for a while. However, when I installed lucid (fresh install) conky starts wrong with ubuntu, like in a glass box that overlaps any window. The weird thing is that if I kill conky and start it over again manually (without the script in preferences->startup applications) it is OK.

I attach screenshots to clarify. Any ideas?

Thanks in advance.

[http://img526.imageshack.us/f/pantallazoyp.png/](http://img526.imageshack.us/f/pantallazoyp.png/)
[http://img687.imageshack.us/i/pantallazobien.png/](http://img687.imageshack.us/i/pantallazobien.png/)

```
# Rendimiento
update_interval 1.0
total_run_times 0
double_buffer yes

background yes
use_xft yes
xftfont HandelGotD:size=9
xftalpha 0.5

# Ejecutarlo en su propia ventana en lugar de usar el escritorio.
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

minimum_size 200 5
maximum_width 250
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color red
default_outline_color white
alignment top_right
gap_x 20
gap_y 40
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale yes

TEXT
${color red}${font openlogos:size=24}K${color orange}${font impact:bold size=30}${execi 3600 cat /etc/issue.net}$font$color
#
RENDIMIENTO ${hr 2}
${font StyleBats:size=18}A${font} CPU total $alignr ${cpu cpu0}%
${cpugraph cpu0 eeeeee F57900 FCAF3E}
${font StyleBats:size=18}A${font} CPU 1 ${cpu cpu1}% ${font weather:size=10}y${font} ${execi 5 sensors |grep "Core 0"|cut -c15-16
} C ${alignr}${cpubar cpu1 12,60}
${font StyleBats:size=18}A${font} CPU 2 ${cpu cpu2}% ${font weather:size=10}y${font} ${execi 5 sensors |grep "Core 1"|cut -c15-16
} C ${alignr}${cpubar cpu2 12,60}
${font StyleBats:size=18}A${font} CPU 3 ${cpu cpu3}% ${font weather:size=10}y${font} ${execi 5 sensors |grep "Core 2"|cut -c15-16
} C ${alignr}${cpubar cpu3 12,60}
${font StyleBats:size=18}A${font} CPU 4 ${cpu cpu4}% ${font weather:size=10}y${font} ${execi 5 sensors |grep "Core 3"|cut -c15-16
} C ${alignr}${cpubar cpu4 12,60}
${font StyleBats:size=16}g${font} RAM $alignc $mem / $memmax $alignr $memperc%
$membar
TEMPERATURAS ${hr 2}
${font weather:size=24}y${font} Nvidia $alignr ${execi 5 nvidia-settings -q GPUCoreTemp|grep Attribute|cut -c44-45
} C
${font weather:size=24}y${font} sda $alignr ${execi 5 nc localhost 7634 | cut -c23-24 } C
${font weather:size=24}y${font} sdb $alignr ${execi 5 nc localhost 7634 | cut -c51-52 } C

#
PROCESOS${hr 2}
${font PizzaDude Bullets:size=16}N${font} ${color}Por CPU%
${color} ${top name 1} $alignr ${top cpu 1}
${color} ${top name 2} $alignr ${top cpu 2}
${color} ${top name 3} $alignr ${top cpu 3}
${font PizzaDude Bullets:size=16}O${font} ${color}Por RAM:
${color} ${top_mem name 1}$alignr ${top_mem mem_res 1}
${color} ${top_mem name 2}$alignr ${top_mem mem_res 2}
${color} ${top_mem name 3}$alignr ${top_mem mem_res 3}
#
DISCOS${hr 2}
${font Pie charts for maps:size=14}7${font} / $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
${fs_bar /}
${font Pie charts for maps:size=14}7${font} home $alignc ${fs_used /home/} / ${fs_size /home/} $alignr ${fs_free_perc /home/}%
${fs_bar /home/}
${font Pie charts for maps:size=14}7${font} 400gb $alignc ${fs_used /media/400gb} / ${fs_size /media/400gb} $alignr ${fs_free_perc /media/400gb}%
${fs_bar /media/400gb}
${font Pie charts for maps:size=14}7${font} 900gb $alignc ${fs_used /media/900gb} / ${fs_size /media/900gb} $alignr ${fs_free_perc /media/900gb}%
${fs_bar /media/900gb}
${font Pie charts for maps:size=14}7${font} IO $alignc ${fs_used /media/IOMEGA_HDD} / ${fs_size /media/IOMEGA_HDD} $alignr ${fs_free_perc /media/IOMEGA_HDD}%
${fs_bar /media/IOMEGA_HDD}
#
RED${hr 2}
${color}${font PizzaDude Bullets:size=14}b${font}IP Pública: ${color}${execi 3600 /home/larry/scripts/myip.sh}
${color}${color}${font PizzaDude Bullets:size=14}a${font}IP Privada: ${color}${addr eth0}
${color}Down:${color} ${downspeed eth0} k/s $alignr${color} Up:${color} ${upspeed eth0} k/s
${color}${downspeedgraph eth0 27,120 F57900 FCAF3E eeeeee 180} $alignr${color}${upspeedgraph eth0 27,120 F57900 FCAF3E eeeeee 25}
${color}${totaldown eth0} $alignr${color}${totalup eth0}
```

---

### Post by wojox on 2010-06-06
I think the first one looks sharp. Let me check my .conkyrc file.

---

### Post by stinkeye on 2010-06-06
Screenshots?
and your conkyrc would help.

---

### Post by primolarry on 2010-06-06
> **wojox said:**
> I think the first one looks sharp. Let me check my .conkyrc file.

Well, the problem is that it overlaps any window:

No window:
[http://img218.imageshack.us/i/pantallazor.png/](http://img218.imageshack.us/i/pantallazor.png/)

Firefox opened:
[http://img693.imageshack.us/i/pantallazo1c.png/](http://img693.imageshack.us/i/pantallazo1c.png/)

Thanks

---

### Post by VCoolio on 2010-06-06
The 'glass' thing is compiz drawing shadows around the conky window. Disable that in the window decorations plugin, add something like ```
!(class=Conky)
```

The problem that conky overlaps is probably caused by the fact that it is started before the window manager (compiz) is done. Add a delay line to a conky startup script and add that to startup applications:
```

#!/bin/bash
sleep 20 && conky -c /path/to/conkyrc
```
Or try to mess with the own_window_type (try normal, dock)

---

### Post by wojox on 2010-06-06
> **primolarry said:**
> Well, the problem is that it overlaps any window:


Okay I gotcha.

---

### Post by primolarry on 2010-06-06
> **VCoolio said:**
> The 'glass' thing is compiz drawing shadows around the conky window. Disable that in the window decorations plugin, add something like ```
!(class=Conky)
```

The problem that conky overlaps is probably caused by the fact that it is started before the window manager (compiz) is done. Add a delay line to a conky startup script and add that to startup applications:
```

#!/bin/bash
sleep 20 && conky -c /path/to/conkyrc
```
Or try to mess with the own_window_type (try normal, dock)

Hello,

I tried all those things:

-I inserted the line in the window decoration plugin
-I tried normal, dock modes. Normal changes nothing, and dock does set it right but in the left side.
-I already had a script like the one you posted, and I found out something interesing: it doesn't matter the time I specify, as the window manager doesn't seem to start after conky starts. If I set up 20 seconds for instance, the desktop is freezed (I can only see gnome do), then conky starts, then the window manager

Any other idea?

Thanks for the help, regards

---

### Post by stinkeye on 2010-06-10
Try using this script to start conky.
It won't start conky until compiz is loaded.
[COLOR="Red"]**It requires the compiz plugin Dbus to be running. (CCSM > utility > Dbus)**[/COLOR]

```
#! /bin/bash
until [ "$done" = "true" ]
do
	if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
	then
		DISPLAY=:0.0 conky -c [COLOR="Magenta"]~/conky/democonky[/COLOR] >/dev/null 2>&1 &
                
                
		done="true";
	else
		echo "CONKY IS WAITING"
		done="false"
		sleep 5;
	fi
done
exit 0
```
[COLOR="#ff00ff"]# Change to the path for your conky[/COLOR]

Save as startconky or whatever you like, make executable and 
link to it in startup applications.

Also I use **own_window_type normal** with no problems.

---

### Post by primolarry on 2010-09-19
hi,

Thanks a lot stinkeye, it worked.

Regards

---

