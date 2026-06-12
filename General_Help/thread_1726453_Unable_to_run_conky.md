---
title: "Unable to run conky"
date: 2011-04-11
forum: General Help
---

### Post by karthick87 on 2011-04-11
These are my results when i type conky in terminal.

```
karthick@karthick:~$ conky
Conky: can't open '/sys/class/hwmon/hwmon2/temp1_input': No such file or directory
please check your device or remove this var from Conky
Conky: Error destroying thread
Conky: Error destroying thread
Conky: Error destroying thread
Conky: Error destroying thread
***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_context_free();

    With the parameter:

    context

    being NULL. Please fix your program.
```

Can someone help?

---

### Post by TeoBigusGeekus on 2011-04-11
Can you post us your conkyrc?

---

### Post by karthick87 on 2011-04-11
```
use_xft yes
xftfont Liberation Sans:size=8
override_utf8_locale yes

text_buffer_size 2048
update_interval 5
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

alignment top_right
gap_x 25
gap_y 35
minimum_size 182 0
maximum_width 182

imlib_cache_size 0

TEXT
${font Liberation Sans:style=Bold:size=8}SYSTEM $stippled_hr${font}
${color0}${font Poky:size=15}S${font}${color}${goto 32}${voffset -8}Kernel:  ${alignr}${color2}${kernel}${color}
${goto 32}Uptime: ${alignr}${color2}${uptime}${color}
${offset 1}${color0}${font Poky:size=16}P${font}${offset -19}${voffset 9}${cpubar cpu0 4,18}${color}${voffset -15}${voffset -1}${goto 32}CPU1: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu1}%${color}${font} ${alignr}${color2}${cpugraph cpu1 8,60 CE5C00 E07A1F}${color}
${voffset -1}${goto 32}CPU2: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu2}%${color}${font} ${alignr}${color2}${cpugraph cpu2 8,60 CE5C00 E07A1F}${color}
${color0}${font Poky:size=16}M${font}${color}${goto 32}${voffset -7}RAM: ${font Liberation Sans:style=Bold:size=8}${color1}$memperc%${color}${font}
${offset 1}${voffset 2}${color2}${membar 4,18}${color}${goto 32}${voffset -2}F: ${color2}${memeasyfree}${color} U: ${color2}${mem}${color}
${voffset 2}${color0}${font Poky:size=15}a${font}${color}${goto 32}${voffset -10}Processes: ${color2}${alignr 13}CPU${alignr}RAM${color}
${voffset -1}${goto 42}${color2}${top name 1}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 1}${alignr }${top mem 1}${color}${font}
${voffset -1}${goto 42}${color2}${top name 2}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 2}${alignr }${top mem 2}${color}${font}
${voffset -1}${goto 42}${color2}${top name 3}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 3}${alignr }${top mem 3}${color}${font}
${voffset -1}${goto 42}${color2}${top name 4}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 4}${alignr }${top mem 4}${color}${font}
${voffset -1}${goto 42}${color2}${top name 5}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 5}${alignr }${top mem 5}${color}${font}

${font Liberation Sans:style=Bold:size=8}Temperature $stippled_hr
${color2}${font Weather:size=60}y${offset 3}${voffset -55}${font Liberation Sans:size=8}${color cccccc}CPU 1 Temp:${color1}${font Liberation Sans:style=Bold:size=8}                ${hwmon 1 temp 1} °C
${offset 25}${font Liberation Sans:size=8}${color cccccc}CPU 2 Temp:${color1}${font Liberation Sans:style=Bold:size=8}                ${hwmon 2 temp 1} °C 

${offset 27}${font Liberation Sans:size=8}${color cccccc}HDD 1 Temp:${color1}${font Liberation Sans:style=Bold:size=8}               ${hddtemp /dev/sda} °C
${offset 27}${font Liberation Sans:size=8}${color cccccc}HDD 2 Temp:${color1}${font Liberation Sans:style=Bold:size=8}               ${hddtemp /dev/sdb} °C 
${voffset 4}${font Liberation Sans:style=Bold:size=8}${color cccccc}DATE $stippled_hr${font}
${voffset -10}${alignc 90}${color2}${font Comic Sans MS:size=47:style=bold}${time %H:%M}${font}${color}

${offset 5}${voffset -6}${color0}${font Poky:size=15}d${font}${color}${offset 40}${voffset -6}${font Liberation Mono:size=11}${alignc}${time %d %B %Y}
${voffset 4}${font Liberation Sans:style=Bold:size=8}RHYTHMBOX $stippled_hr${font}
${execpi 10 ~/.conkycolors/scripts/conkyRhythmbox.py -t ~/.conkycolors/templates/conkyRhythmbox.template}
${voffset 4}${font Liberation Sans:style=Bold:size=8}HD $stippled_hr${font}
${execpi 30 ~/.conkycolors/bin/conkyHD1}
```

---

### Post by TeoBigusGeekus on 2011-04-11
```
#${color2}${font Weather:size=60}y${offset 3}${voffset -55}${font Liberation Sans:size=8}${color cccccc}CPU 1 Temp:${color1}${font Liberation Sans:style=Bold:size=8}                ${hwmon 1 temp 1} °C
#${offset 25}${font Liberation Sans:size=8}${color cccccc}CPU 2 Temp:${color1}${font Liberation Sans:style=Bold:size=8}                ${hwmon 2 temp 1} °C 
```

These two lines are problematic. Delete them and it should work OK.
In order to monitor CPU temperature, I'd suggest installing lmsensors and trying to use the command sensors with grep and cut in your conky.
Example from my conky
```
execi 60 sensors|grep temp2|cut -c 14-21
```
that isolates the cpu temp and cuts it to my needs. You'll have to modify this of course according to your sensors output in order to work.

---

### Post by karthick87 on 2011-04-11
Thankyou :) But now i dont get the symbol for temperature...Why? I have attached my snapshot,have a look at it.

---

### Post by TeoBigusGeekus on 2011-04-11
After this
```
${font Liberation Sans:style=Bold:size=8}Temperature $stippled_hr
```
line, add this
```
${color2}${font Weather:size=60}y${offset 3}${voffset -55}
```

---

### Post by Cypher2 on 2011-04-16
Hello guys,

I pretty much stumbled on this same issue after finishing my conkyrc and rebooting.

It<s apparently known to be a Debian node mapping issue.

In my personal case, hwmon1 and hwmon2  (CPU and ACPI) end up switching places every couple of reboots AND IT SUCKS!

What I tried enabling was an if_file argument involving the *_input locations according to what the boot process loaded up but still that was a no go.

Can you tell me if the logic is correct though?

...color/font format....${if_file /sys/class/hwmon/hwmon1/temp1_input}${hwmon 1 temp 1}${else}${hwmon 2 temp 1}${endif}

Is there anyway to symlink the devices contents from hm1 to hm2 and vice versa maybe?

Thanks :)


Edit: I've just stumbled upon this: [http://ubuntuforums.org/showthread.php?t=1534729&highlight=Conky+hwmon](http://ubuntuforums.org/showthread.php?t=1534729&highlight=Conky+hwmon)

---

