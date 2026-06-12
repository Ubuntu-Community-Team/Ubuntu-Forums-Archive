---
title: "Conky not working after upgrading to kernel 3.0.1 in Ubuntu 11.04"
date: 2011-08-14
forum: General Help
---

### Post by johnjanney on 2011-08-14
I upgraded my Ubuntu 11.04 laptop to kernel 3.0.1 and when I try to start Conky using my custom conkyrc, the conky process dies. I played around with it and discovered (through trial and error testing) that the code for the CPU temperature crashes conky. It worked before the upgrade. 

Any idea what's going on or how I can get the CPU temp monitoring working again in kernel 3.0.1?

Here is the code that is crashing conky:

```

${GOTO 5}Core1:${GOTO 75}${hwmon 1 temp 1} ºF
${GOTO 5}Core2:${GOTO 75}${hwmon 2 temp 1} ºF

```

Here is the entire conkyrc:

```

######################
# - Conky settings - #
######################
temperature_unit fahrenheit
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
minimum_size 182 800
maximum_width 182

default_bar_size 60 8

#########################
# - Graphics settings - #
#########################
draw_shades no

default_color cccccc

color0 white
color1 E07A1F
color2 white

# OLD DEFAULT CONKYRC CODE
#background yes
#use_xft yes
#xftfont HandelGotD:size=9
#xftalpha 0.5
#update_interval 1.0
#total_run_times 0
#own_window yes
#own_window_type normal
#own_window_transparent yes
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#double_buffer yes
#minimum_size 200 5
#maximum_width 200
#draw_shades no
#draw_outline no
#draw_borders no
#draw_graph_borders no
#default_color white
#default_shade_color red
#default_outline_color green
#alignment top_right
#gap_x 12
#gap_y 48
#no_buffers yes
#uppercase no
#cpu_avg_samples 2
#override_utf8_locale no

TEXT
SYSTEM $stippled_hr
$sysname $kernel on $machine

Uptime $alignr $uptime
Load $alignr $loadavg
#Hostname $alignr $nodename

NETWORK $stippled_hr
IP: ${addr wlan0}
Signal: ${wireless_link_qual_perc wlan0}
Down: ${downspeed wlan0} Kb/s ${alignr}Up: ${upspeed wlan0} Kb/s
${downspeedgraph wlan0 15,50 ffffff ffffff} ${alignr}${upspeedgraph wlan0 15,50 ffffff ffffff}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}

TEMPERATURES $stippled_hr
#${GOTO 5}Core1:${GOTO 75}${hwmon 1 temp 1} ºF
#${GOTO 5}Core2:${GOTO 75}${hwmon 2 temp 1} ºF
${GOTO 5}Hard disk:${GOTO 75}${hddtemp /dev/sda} ºF

${voffset 4}WEATHER $stippled_hr
${execi 1800 /home/johnjanney/.conky/weather/weather.sh}

```

---

### Post by 3rdalbum on 2011-08-15
Do you have the kernel module for the hardware sensors? In other words, if you run the 'sensors' command, does it work?

---

### Post by johnjanney on 2011-08-15
Yes. 

johnjanney@johnjanney-Gateway-M290:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +48.0°C  (crit = +86.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +47.0°C  (high = +85.0°C, crit = +85.0°C)  
Core 1:      +47.0°C  (high = +85.0°C, crit = +85.0°C)  

johnjanney@johnjanney-Gateway-M290:~$

---

### Post by johnjanney on 2011-08-17
Still doesn't work. Every time I remove the # from in front those lines, conky crashes. I've searched online and haven't found any solution. I get results when I type "sensors" in terminal. Do I need to uninstall, then reinstall conky?

---

### Post by Habitual on 2011-08-18
how about /path/to/sensors in your rc file? Does that help?

---

### Post by johnjanney on 2011-08-18
I'm new to conky... how/where would I add /usr/bin/sensors in the conkyrc file?

---

### Post by Habitual on 2011-08-18
I mis-spoke.
The problem may be "Core1" and "Core2"
try Core0 and Core1 at
```

${GOTO 5}Core1:${GOTO 75}${hwmon 1 temp 1} ºF
${GOTO 5}Core2:${GOTO 75}${hwmon 2 temp 1} ºF

```

I don't know where sensors came from unless it's part of what is supposed to supply hwmon.

---

### Post by johnjanney on 2011-08-18
Nope. Still kills conky. Before upgrading the kernel, it worked. I also tried changing "hwmon 1" to "hwmon 0" and "hwmon 2" to "hwmon 1" and got the same result -- kills conky.

also, I commented out the hwmon parts and the "Core" parts show up. I think those are just text/labels. 

```

${GOTO 5}Core 1:#${GOTO 75}${hwmon 1 temp 1} ºF

${GOTO 5}Core 2:#${GOTO 75}${hwmon 2 temp 1} ºF

```

---

### Post by johnjanney on 2011-08-18
I found this
[http://ubuntuforums.org/showthread.php?p=10820997](http://ubuntuforums.org/showthread.php?p=10820997)

and got the first one working with the following code:

```

${GOTO 5}Core 0:${GOTO 75}${hwmon 0 temp 1} ºF

${GOTO 5}Core 1:#${GOTO 75}${hwmon 1 temp 0} ºF

```

but when I uncomment the second line, it kills conky.

```

${GOTO 5}Core 1:${GOTO 75}${hwmon 1 temp 0} ºF

```

Very strange... why won't it allow me to see the second core?

In /sys/class/hwmon/ I have hwmon0 and hwmon1.

---

### Post by Habitual on 2011-08-18
> **johnjanney said:**
> ...Very strange... why won't it allow me to see the second core?

Linux starts counting at zero, not one, so conky is coded to see 2 Cores.

---

### Post by johnjanney on 2011-08-18
I understand, but does that explain why it won't show Core 1 (the second core)? Before upgrading the kernel, it was showing both cores.

---

### Post by Habitual on 2011-08-18
Is this a dual-core processor?

If it is, there may only be 1 fan control.

"hwmon0"

---

### Post by johnjanney on 2011-08-18
I believe it is dual core, yes. Before upgrading, conky showed both cores' temps. Now, it only will show one. Very strange.

Here is what I get when I type in "sensors" in terminal. 

> 
johnjanney@johnjanney-Gateway-M290:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +51.0°C  (crit = +86.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +51.0°C  (high = +85.0°C, crit = +85.0°C)  
Core 1:      +51.0°C  (high = +85.0°C, crit = +85.0°C)  

johnjanney@johnjanney-Gateway-M290:~$ 


---

### Post by Habitual on 2011-08-20
I have a dual-core processor also, but only 1 fan.
Check the specs for the system/mobo.

---

