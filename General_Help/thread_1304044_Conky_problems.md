---
title: "Conky problems"
date: 2009-10-28
forum: General Help
---

### Post by dbyjazz on 2009-10-28
I installed Conky and I reboot but I can't find it anywhere. I go to System Tools and not there, tried adding it. Added it to Startup Applications and doesn't work either.

In command I type 'Conky' and I get the message..

> Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: forked to background, pid is 2673
derek@derek-laptop:~$ 
Conky: desktop window (20000a8) is subwindow of root window (6c)
Conky: window type - override
Conky: drawing to created window (0x4400001)
Conky: drawing to double buffer
Conky: obj->data.cpu_index 2 info.cpu_count 1
**Conky: attempting to use more CPUs than you have!**

Here's my output of .conkyrc (~)-gedit or *'gedit ~/.conkyrc'*...

```
background yes
use_xft yes
xftfont DejaVu Sans Mono:size=8
xftalpha 0.8
out_to_console no
update_interval 5.0
total_run_times 0
draw_shades no

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

double_buffer yes
default_color 586F86
color1 white
alignment bottom_left
gap_x 2
gap_y 2
#no_buffers yes
use_spacer yes

TEXT
$nodename:${color1}$kernel${color} up:${color1}$uptime${color} cpu1:${color1}${cpu cpu1}% ${cpubar 6,30 cpu1}${freq cpu1}MHz${color} cpu2:${color1}${cpu cpu2}% ${cpubar 6,30 cpu2}${freq cpu2}MHz${color} mem:${color1}$memperc% ${membar 6,30}${color} dsk:${color1}${fs_used /}/${fs_size /}${fs_bar 6,30 /}${color} load:${color1}$loadavg ${color} ip:${color1}${addr wlan0}${color} trafc:${color1}${downspeed wlan0}/${upspeed wlan0}Kb/s${color} bat:${color1}$battery`
```

edit: If I'm correct I'm supposed to delete everything that has to do with 'cpu2' under 'text' but I'm not sure what to delete exactly.

---

### Post by TheNessus on 2009-10-28
TEXT
$nodename:${color1}$kernel${color} up:${color1}$uptime${color} cpu1:${color1}${cpu cpu1}% ${cpubar 6,30 cpu1}${freq cpu1}MHz${color} **cpu2:${color1}${cpu cpu2}% ${cpubar 6,30 cpu2}${freq cpu2}MHz${color}** mem:${color1}$memperc% ${membar 6,30}${color} dsk:${color1}${fs_used /}/${fs_size /}${fs_bar 6,30 /}${color} load:${color1}$loadavg ${color} ip:${color1}${addr wlan0}${color} trafc:${color1}${downspeed wlan0}/${upspeed wlan0}Kb/s${color} bat:${color1}$battery`[/code]edit: If I'm correct I'm supposed to delete everything that has to do with 'cpu2' under 'text' but I'm not sure what to delete exactly.

delete that

---

### Post by dbyjazz on 2009-10-28
still can't find it anywhere. thanks though! It got rid of that error

---

### Post by dbyjazz on 2009-10-28
someone please help. there's like nothing on google with my specific issue

---

### Post by sailthesea on 2009-10-28
d

---

### Post by dbyjazz on 2009-10-28
> **sailthesea said:**
> Terminal: conky

You did try that I hope;)

yep I did :D

from above is the fist time I tried it. This is what I'm getting now..

```
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: forked to background, pid is 2942
derek@derek-laptop:~$ 
Conky: desktop window (20000a8) is subwindow of root window (6c)
Conky: window type - override
Conky: drawing to created window (0x4800001)
Conky: drawing to double buffer
```

---

### Post by DarkAmbient on 2010-01-15
incase you havnt solved the problem yet, I mng to get conky working by commenting out these two lines in ~.conkyrc .

```
##${goto 32}CPU2: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu2}%${color}${font} ${alignr}${color2}
##${cpugraph cpu2 8,60 CE5C00 E07A1F}${color}
```

hope this helps.

---

