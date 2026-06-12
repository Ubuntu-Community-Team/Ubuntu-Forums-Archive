---
title: "Conky on top of windows at boot"
date: 2010-07-26
forum: General Help
---

### Post by gannggstaz on 2010-07-26
Every time I boot, conky (the system manager tool) is on top of all other windows. Every time I restart conky (save the .conkyrc file) it ends up under all the windows. 
Here is my conkyrc up to the TEXT part:
```
######################
# - Conky settings - #
######################
update_interval 1
total_run_times 0
net_avg_samples 1
cpu_avg_samples 1

imlib_cache_size 0
double_buffer yes
no_buffers yes

#####################
# - Text settings - #
#####################
use_xft yes
xftfont Liberation Sans:size=8
override_utf8_locale yes
text_buffer_size 2048

#############################
# - Window specifications - #
#############################
own_window_class Conky
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

alignment top_right
gap_x 25
gap_y 40
# minimum_size 182 0
maximum_width 300

default_bar_size 60 8

#########################
# - Graphics settings - #
#########################
draw_shades no

default_color cccccc

color0 white
color1 fuchisa
color2 white
```If nothing else, is there some command I that restarts conky other than saving the conkyrc file?

---

### Post by themusicalduck on 2010-07-26
You need to start Conky with a delay. If you make an empty text file and paste ```
#!/bin/bash
sleep 30 && conky ;
``` into it, then save it as a name with .sh on the end. Then you can set that script to run on startup instead of just "conky".

It might work to just put ```
sleep 30 && conky
``` into the code box for the startup preferences as well, but I haven't actually tried it that way.

---

### Post by Covi on 2010-09-17
BUMP! still it works ok.
Seems issue related with Compiz: must be initiated after it.
[http://ubuntuforums.org/showpost.php?p=5609577&postcount=4](http://ubuntuforums.org/showpost.php?p=5609577&postcount=4)

Thanks ;)

---

### Post by Murdock304 on 2011-01-10
I've been banging my head against this for the last few hours. Thank you, this shell script solution with sleep works well!

---

### Post by Wipster on 2011-02-07
Hi,
I am having the same problem but the solutions mentioned are having no effect. own_window_type is on override, I have tried changing my launcher sleep time 35 seconds, even though I have a usable desktop at 10 ish, I have even tried applying window rules in CCSM to class=Conky for below.

The only resolve is to restart conky :| also it seems that seemingly randomly it will pop above the other windows again... here are my conky settings.
```

####
## Use XFT? Required to Force UTF8 (see below).
#
use_xft yes
xftfont DroidSans:size=8.75
xftalpha 0.1
text_buffer_size 2048

####
## Force UTF8? Requires XFT (see above).
## Displays degree symbol, instead of Â°, etc.
#
override_utf8_locale yes

####
## Daemonize Conky, aka 'fork to background'.
#
background yes

####
## Update interval in seconds.
#
update_interval 1.5

####
## This is the number of times Conky will update before quitting.
## Set to zero to run forever.
#
total_run_times 0

####
## Create own window instead of using desktop (required in nautilus)?
#
own_window yes
own_window_type override
own_window_transparent yes

####
## Force images to redraw when they change.
#
imlib_cache_size 0

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
alignment top_right

####
## Minimum size of text area.
#
minimum_size 238 0

####
## Gap between text and screen borders.
#
gap_x 8
gap_y 33

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
border_inner_margin 4

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
color8 DarkSlateGray
color9 Black

####
## Load Lua for bargraphs (required).
## Set the path to your script here.
#
lua_load ~/.conky/scripts/bargraph.lua
lua_draw_hook_post main_bars

####
## Installed fonts (required).
#
# ConkyWeather (Stanko Metodiev)
# ConkyWindNESW (Stanko Metodiev)
# Cut Outs for 3D FX (Fonts & Things)
# Droid Font Family (Google Android SDK)
# Liberation Mono (Ascender Corp)
# Liberation Sans (Ascender Corp)
# Moon Phases (Curtis Clark)
# OpenLogos (Icoma)
# PizzaDude Bullets (Jakob Fischer)
# Radio Space (Iconian Fonts)
# StyleBats (Vinterstille)
# Ubuntu (Canonical Ltd)
# Ubuntu Title Bold (Paulo Silva)
# Weather (Jonathan Macagba)

TEXT
##################
##    SYSTEM    ##
##################
${font DroidSans:bold:size=8.25}${color4}SYSTEM${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font OpenLogos:size=10}${color2}u${voffset -4}${font DroidSans:size=8.65}${color3}${offset 5}${sysname}${offset 5}${kernel}${alignr}${font DroidSans:size=8.75}${machine}${font}
${voffset 2}${font StyleBats:size=10}${color2}A${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}Intel${offset 3}Core${offset 3}2${offset 3}P8700${alignr}${font DroidSans:size=8.4}${freq_g cpu0}${offset 1}GHz${font}
${voffset 2}${font StyleBats:size=10}${color2}q${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}System${offset 3}Uptime${alignr}${font DroidSans:size=8.4}${uptime_short}${font}
##################
##  PROCESSORS  ##
##################
${voffset 6}${font DroidSans:bold:size=8}${color4}PROCESSORS${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=10}${color2}k${voffset -2}${font DroidSans:size=8.4}${color3}${offset 2}CPU1${offset 5}${font DroidSans:size=8.55}${cpu cpu1}%${font}
${voffset 2}${font StyleBats:size=10}${color2}k${voffset -2}${font DroidSans:size=8.4}${color3}${offset 2}CPU2${offset 5}${font DroidSans:size=8.55}${cpu cpu2}%${font}
${voffset 2}${font StyleBats:size=10}${color2}j${voffset -2}${font DroidSans:size=8.4}${color3}${offset 2}TEMP${offset 5}${font DroidSans:size=8.55}${execi 4 i8kctl | cut --delimiter=" " -f 4}°C${font}
${voffset 2}${font StyleBats:size=10}${color2}o${voffset -2}${font DroidSans:size=8.4}${color3}${offset 2}RPM${offset 5}${font DroidSans:size=8.55}${execi 4 i8kctl | cut --delimiter=" " -f 8}${font}
##################
##    MEMORY    ##
##################
${voffset 6}${font DroidSans:bold:size=8}${color4}MEMORY${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=10}${color2}l${voffset -2}${font DroidSans:size=8.4}${color3}${offset 3}RAM${goto 97}${font DroidSans:size=8.55}${mem}${goto 133}/${offset 5}${memmax}${alignr}${memperc}%${font}
##################
# TOP PROCESSES ##
##################
${voffset 16}${font DroidSans:bold:size=8}${color4}TOP PROCESSES${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 1}${goto 120}${font DroidSans:size=8.55}${top_mem mem_res 1}${alignr}${top_mem mem 1}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 2}${goto 120}${font DroidSans:size=8.55}${top_mem mem_res 2}${alignr}${top_mem mem 2}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 3}${goto 120}${font DroidSans:size=8.55}${top_mem mem_res 3}${alignr}${top_mem mem 3}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 4}${goto 120}${font DroidSans:size=8.55}${top_mem mem_res 4}${alignr}${top_mem mem 4}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 5}${goto 120}${font DroidSans:size=8.55}${top_mem mem_res 5}${alignr}${top_mem mem 5}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 6}${goto 120}${font DroidSans:size=8.55}${top_mem mem_res 6}${alignr}${top_mem mem 6}%${font}
##################
##     HDD      ##
##################
${voffset 16}${font DroidSans:bold:size=8}${color4}HDD${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 5}${font StyleBats:size=10}${color2}x${voffset -2}${font DroidSans:size=8.4}${color3}${offset 4}DRIVE${goto 95}${font DroidSans:size=8.55}${fs_used /}${goto 133}/${offset 5}${fs_size /}${alignr}${fs_free_perc /}%${font}
${voffset 15}${font StyleBats:size=10}${color2}4${voffset -2}${font DroidSans:size=8.4}${color3}${offset 4}SWAP${goto 95}${font DroidSans:size=8.55}${swap}${goto 133}/${offset 5}${swapmax}${alignr}${swapperc}%${font}

```

---

### Post by stinkeye on 2011-02-07
Try changing...
```
own_window_type override
```

to
```
own_window_type normal
```


and add
```
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

---

### Post by Wipster on 2011-02-07
Ahha getting closer the window now starts in the background when booting havn't tested for long to see if it pops forward, but its also affected by the show desktop minimise button.

Edit:- No sooner have I posted but a quick google and I get the answer;

For the issue of conky disappearing on 'show desktop' button go to system > preferences > compiz config settings manager > general options find the check box for "hide skip taskbar windows" and make sure it is unchecked.

Win, why on earth did other solutions not work I wonder.

---

### Post by stinkeye on 2011-02-07
I see a lot of people using **own_window_type override** with no problems
but always gives me trouble.

"Override windows are not under the control of the window manager"

This is useful, as compiz won't draw a shadow around the window and it is not included when showing the desktop.

But as you found out when using **own_window_type normal** you just
exclude conky from drawing shadows in the window decorations 
plugin and uncheck the **hide skip taskbar windows** setting.

You can also use this script to start conky as soon as compiz is loaded.
[SIZE="3"][COLOR="Red"]You need to enable the **Dbus** plugin in ccsm.[/COLOR][/SIZE]
Save as start_conky and make executable.
```
#! /bin/bash
until [ "$done" = "true" ]
do
	if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
	then
               
		DISPLAY=:0.0 [COLOR="Magenta"]conky -c ~/conky/conkypanel[/COLOR] >/dev/null 2>&1 &
                
                
		done="true";
	else
		echo "CONKY IS WAITING"
		done="false"
		sleep 5;
	fi
done
exit 0
```
[COLOR="#ff00ff"]Change for the command you use to start conky.[/COLOR]
Add to startup applications.
(...and remove your old start entry for conky in startup applications)

---

### Post by CK0y0TE on 2013-01-24
Another option besides the additional startup script is that conky provides its own startup delay by the '-p' parameter.

However, the script above guarantees conky will never ever start before compiz is ready to receive.
While the '-p'  may be a quick and easy solution to some of us who are not that keen on bashing with terminal input. 
Then again '-p' might annoy you some day by showing conky on top again. But you can alway increase the delay depending on the initialisation time compiz needs.

So, to do the '-p' option ; just go to your system startup parameters in gnomeshell(or whatever is your gui millage) and add 'conky -p 60' it will start conky with a 60 seconds delay. 

Remeber to point to your own startup script and config file if you have anny. Additionally just move your custom '.conkyrc' file to your home dir and it will take that as a default so you dont have to specify one.
To sum it up: adding 'conky -p 60' is quick,short and easy. Which is my cup of tea...

---

### Post by oldos2er on 2013-01-24
Old thread closed.

---

