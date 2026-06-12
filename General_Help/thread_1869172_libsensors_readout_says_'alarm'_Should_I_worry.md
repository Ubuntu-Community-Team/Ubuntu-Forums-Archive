---
title: "libsensors readout says 'alarm': Should I worry?"
date: 2011-10-25
forum: General Help
---

### Post by airspoon on 2011-10-25
Hello, 

I just recently installed libsensors4 from the terminal. I then configured and ran it, mainly to get an idea of my CPU temperatures. I recently installed Ubuntu 11.10 on an older machine with a Core 2 Duo (E6600) 2.4 ghz and this CPU was almost constantly running pretty hot under Vista (about 85c). 

So far, the temps look really good and I was relieved. However, what I'm assuming to be the voltage, has the word 'ALARM' on several lines.

Here is the readout:
```

fx510x:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +56.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +51.0°C  (high = +84.0°C, crit = +100.0°C)

emc6d103-i2c-3-2e
Adapter: SMBus I801 adapter at 4000
in0:          +1.51 V  (min =  +0.00 V, max =  +3.32 V)  ALARM
in1:          +1.14 V  (min =  +0.00 V, max =  +2.99 V)  ALARM
in2:          +3.30 V  (min =  +0.00 V, max =  +4.38 V)
in3:          +5.06 V  (min =  +0.00 V, max =  +6.64 V)  ALARM
in4:         +11.98 V  (min =  +0.00 V, max = +15.94 V)  ALARM
fan1:         856 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:         878 RPM  (min =    0 RPM)
fan4:           0 RPM  (min =    0 RPM)
temp1:        +34.2°C  (low  = -127.0°C, high = +127.0°C)
temp2:        +29.1°C  (low  = -127.0°C, high = +127.0°C)
temp3:        +41.2°C  (low  = -127.0°C, high = +127.0°C)
cpu0_vid:    +0.000 V

```

Is this something I need to worry about? It doesn't look at that close to listed max figures, but I'm not sure if they are higher than what they are supposed to be and how serious I should take the 'ALARM' messages. 

Thanks for any and all help.

---

### Post by TeoBigusGeekus on 2011-10-25
Here's my output
```
w83627hf-isa-0290
Adapter: ISA adapter
in0:          +1.44 V  (min =  +2.99 V, max =  +3.39 V)  ALARM
in1:          +1.46 V  (min =  +2.99 V, max =  +3.39 V)  ALARM
in2:          +3.38 V  (min =  +2.82 V, max =  +3.79 V)
in3:          +2.99 V  (min =  +0.13 V, max =  +1.55 V)  ALARM
in4:          +3.22 V  (min =  +0.34 V, max =  +0.02 V)  ALARM
in5:          +3.23 V  (min =  +0.34 V, max =  +2.18 V)  ALARM
in6:          +3.23 V  (min =  +1.55 V, max =  +0.19 V)  ALARM
in7:          +3.36 V  (min =  +2.06 V, max =  +0.35 V)  ALARM
in8:          +3.49 V  (min =  +0.13 V, max =  +1.02 V)  ALARM
fan1:           0 RPM  (min = 8437 RPM, div = 8)  ALARM
fan2:        2220 RPM  (min = 3515 RPM, div = 8)  ALARM
fan3:           0 RPM  (min = 10546 RPM, div = 2)  ALARM
temp1:        +30.0°C  (high = +40.0°C, hyst = -121.0°C)  sensor = thermistor
temp2:        +47.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
temp3:        +66.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:    +1.388 V
beep_enable: enabled
```
It's been like this for as long as I can remember.
So, yep, don't worry about it.

---

### Post by airspoon on 2011-10-25
Thanks, that makes me feel better at least.

---

### Post by cryptotheslow on 2011-10-25
If it really bothers you - once you've worked out which temp / voltage sensor is which you can customise the libsensors configuration in libsensors.conf so the labels make sense and the useless sensors aren't shown.

This might help:
[http://manpages.ubuntu.com/manpages/maverick/man5/sensors.conf.5.html](http://manpages.ubuntu.com/manpages/maverick/man5/sensors.conf.5.html)

I know I have one "temp" sensor on mine that permanently shows 66C even from a cold start up lol

I'm sure there's plenty of other guides to it elsewhere as well :D

---

### Post by airspoon on 2011-10-25
Cool, thanks for the link. I'm definitely going to try that out. What about Conky? Can Conky be configured to show these values too? I'm not at all familiar with Conky, but have played with it before and gave up because I couldn't get it to look pretty enough. I might give it another go on this machine.

---

### Post by Mark Phelps on 2011-10-25
I have much the same display. I think the ALARM means that if the voltage exceeds the maximum, some kind of alarm gets triggered.  I also think that you can disable/enable those alarms in your BIOS.  So, all this is really telling you is that alarms have been enabled.

---

### Post by cryptotheslow on 2011-10-25
I've not used Conky myself but I've seen others discussing sensor applets for it - so presume it must be possible.

On 10.04 I think I'm using indicator-applet which can neatly put temps and fan speeds up in the top bar. Don't think the same is compatible with the Unity desktop though. Have also seen screenshots from people who have hacked their way about to use Gnome Shell on 11.x who had neat little temp indicators showing. Seems like a lot of work for a temp reading though!

First thing really is to get the sensors output sane before worrying about where / how to display them :D

Have fun.

---

### Post by TeoBigusGeekus on 2011-10-25
My sensors' output:
```
w83627hf-isa-0290
Adapter: ISA adapter
in0:          +1.44 V  (min =  +2.99 V, max =  +3.39 V)  ALARM
in1:          +1.46 V  (min =  +2.99 V, max =  +3.39 V)  ALARM
in2:          +3.36 V  (min =  +2.82 V, max =  +3.79 V)
in3:          +2.99 V  (min =  +0.13 V, max =  +1.55 V)  ALARM
in4:          +3.23 V  (min =  +0.34 V, max =  +0.02 V)  ALARM
in5:          +3.23 V  (min =  +0.34 V, max =  +2.18 V)  ALARM
in6:          +3.23 V  (min =  +1.55 V, max =  +0.19 V)  ALARM
in7:          +3.36 V  (min =  +2.06 V, max =  +0.35 V)  ALARM
in8:          +3.49 V  (min =  +0.13 V, max =  +1.02 V)  ALARM
fan1:           0 RPM  (min = 8437 RPM, div = 8)  ALARM
fan2:        2220 RPM  (min = 3515 RPM, div = 8)  ALARM
fan3:           0 RPM  (min = 10546 RPM, div = 2)  ALARM
temp1:        +31.0°C  (high = +40.0°C, hyst = -121.0°C)  sensor = thermistor
temp2:        +48.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
temp3:        +67.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:    +1.388 V
beep_enable: enabled
```

I use this line in my conky
```
${execi 60 sensors|grep temp2|cut -c 14-21}
```
to get the temp2 (cpu) temperature.
The line executes sensors every 60 seconds, filters the output to show only the line with the string temp2 in it (grep) and then takes the characters between the 14th and the 21rst (+48.0°C) and prints them on conky.
I don't think it's too difficult to adjust it to your needs.

---

### Post by stinkeye on 2011-10-25
> **airspoon said:**
> Cool, thanks for the link. I'm definitely going to try that out. What about Conky? Can Conky be configured to show these values too? I'm not at all familiar with Conky, but have played with it before and gave up because I couldn't get it to look pretty enough. I might give it another go on this machine.
Yep, I use conky underneath a transparent Unity panel to display
* CPU temp and usage
* HDD and GPU Temps
* mem usage
* net up/down speeds

I like to have all these in the panel so you can easily see them when 
windows are maximized.
The temperatures are passed through scripts to change the color from grey to orange to red, depending on how hot the temps are.
All the info and scripts was gleaned from the huge conky thread in the cafe.

Using your sensors output and temp2
this is a conky config to start you off.
This is only visible through a Unity panel made completely transparent
with ccsm.
```




####
## Use XFT? Required to Force UTF8 (see below).
#
use_xft yes
xftfont Ubuntu:size=10
xftalpha 0.8
text_buffer_size 512

####
## Force UTF8? Requires XFT (see above).
## Displays degree symbol, instead of Â°, etc.
#
override_utf8_locale yes

####
## Daemonize Conky, aka 'fork to background'.
#
background no

####
## Update interval in seconds.
#
update_interval 1.0

####
## This is the number of times Conky will update before quitting.
## Set to zero to run forever.
#
total_run_times 0

####
## Create own window instead of using desktop (required in nautilus)?
#
own_window yes
own_window_colour 031426
own_window_title conkytimer
own_window_type override
own_window_transparent yes
own_window_hints undecorated,above,sticky,skip_taskbar,skip_pager
default_color ffffff
#own_window_argb_visual yes
#own_window_argb_value 180

####
## Use double buffering? Reduces flicker.
#
double_buffer yes

####
## Draw shades?
#
draw_shades no

####
## Draw outlines?
#
draw_outline no

####
## Draw borders around text?
#
draw_borders no
default_outline_color 7E88C4
####
## Draw borders around graphs?
#
draw_graph_borders no

####
## Print text to stdout?
## Print text in console?
#
out_to_ncurses no
out_to_console no

####
## Text alignment.
#
alignment tr

####
## Minimum size of text area.
#
minimum_size 650 20
maximum_width 650

####
## Gap between text and screen borders.
#
gap_x 100
gap_y 

####
## Shorten MiB/GiB to M/G in stats.
#
short_units yes

####
## Pad % symbol spacing after numbers.
#
pad_percents 0

####
## Pad spacing between text and borders.
#
border_inner_margin 2

####
## Limit the length of names in "Top Processes".
#
top_name_width 10

####
## Subtract file system -/+buffers/cache from used memory?
## Set to yes, to produce meaningful physical memory stats.
#
no_buffers yes

####
## Set to yes, if you want all text to be in UPPERCASE.
#
uppercase no

####
## Number of cpu samples to average.
## Set to 1 to disable averaging.
#
cpu_avg_samples 2

####
## Number of net samples to average.
## Set to 1 to disable averaging.
#
net_avg_samples 2

####
## Add spaces to keep things from moving around?
## Only affects certain objects.
#
use_spacer right

####
## My colors (suit yourself).
#
color0 White
color1 Ivory
color2 Ivory2
color3 Ivory3
color4 Tan1
color5 Tan2
color6 Gray
color7 AntiqueWhite4
color8 orange
#color9 red
color9 6A90EF #icon

#lua_load ~/conky/bargraph_smallcpu.lua
#lua_draw_hook_post main_bars

TEXT
${color9}${font ConkySymbols:size=12}f${font}${color}${offset 1}${voffset -2}CPU ${color8}${execpi 5 sensors | grep temp2 | awk '{print $2}' | cut -c2-3}°C${color}


```
Alter the 
```
gap_x 100
gap_y
```
values to position elsewhere on your desktop.

---

