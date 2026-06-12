---
title: "Need help with conky script"
date: 2012-07-01
forum: General Help
---

### Post by GreatDanton on 2012-07-01
[FONT="System"][SIZE="4"]
**[COLOR="DarkOrchid"]EDIT: THE PROBLEM IS NOW SOLVED. TAKE A LOOK AT THE PAGE 5 AND 6 {FROM POSTS 48-52}. THERE ARE INSTRUCTIONS SO EVERYONE COULD HAVE A NICE CONKY LIKE ME!![/COLOR]**
[/SIZE][/FONT]


As the title says I need a little help for conky script. In the attachments you can see my current conky. This is famous VinDSL conky, which I copied. What I wanted to do is to get the weather part working, the calendar has to be moved to the right, and also there is problem with Graphic card, because VinDSL wrote script for his computer (He had nVidia, but I have Ati radeon). I have 3Ghz processor but on conky script there is just 2ghz. Also the auto detection of the system is not working (12.0 alpha 1 -but it has to be 12.04)

I've been searching around how to fix this conky script, but I am new to this and I don't quite understand all text. So can you tell me what is the easiest way to do this?

When I type conky in terminal I got this messages.
```
conky
Package `nvidia-current' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Conky: forked to background, pid is 2757

```

```
Conky: desktop window (1800095) is subwindow of root window (160)
Conky: window type - normal
Conky: drawing to created window (0x4200002)
Conky: drawing to double buffer
/home/jan/.conky/weather/weather.sh: line 149: /usr/bin/curl: No such file or directory
/home/jan/.conky/weather/weather.sh: line 156: /usr/bin/xsltproc: No such file or directory
/home/jan/.conky/weather/weather.sh: line 149: /usr/bin/curl: No such file or directory
/home/jan/.conky/weather/weather.sh: line 156: /usr/bin/xsltproc: No such file or directory
/home/jan/.conky/weather/weather.sh: line 149: /usr/bin/curl: No such file or directory
/home/jan/.conky/weather/weather.sh: line 156: /usr/bin/xsltproc: No such file or directory
/home/jan/.conky/weather/weather.sh: line 149: /usr/bin/curl: No such file or directory
/home/jan/.conky/weather/weather.sh: line 156: /usr/bin/xsltproc: No such file or directory
/home/jan/.conky/weather/weather.sh: line 149: /usr/bin/curl: No such file or directory
/home/jan/.conky/weather/weather.sh: line 156: /usr/bin/xsltproc: No such file or directory
/home/jan/.conky/weather/weather.sh: line 149: /usr/bin/curl: No such file or directory
/home/jan/.conky/weather/weather.sh: line 156: /usr/bin/xsltproc: No such file or directory
/home/jan/.conky/weather/weather.sh: line 149: /usr/bin/curl: No such file or directory
/home/jan/.conky/weather/weather.sh: line 156: /usr/bin/xsltproc: No such file or directory
/home/jan/.conky/weather/weather.sh: line 149: /usr/bin/curl: No such file or directory
/home/jan/.conky/weather/weather.sh: line 156: /usr/bin/xsltproc: No such file or directory

```

If anybody is interested here is my whole conky script:
```
# Conky configuration
alignment top_right
background yes
##################################
## VinDSL | rev. 11-12-01 20:20 ##
##################################
##     December 2011 Series     ##
##################################

## ¡PLEASE READ THE FINE PRINT! ##

####
## Development Platforms (current)
#
#  Ubuntu 10.10 'Maverick Meerkat' (GNOME 2.28 - Conky 1.8.0)
#  Ubuntu 12.04 'Precise Pangolin' (GNOME-SHELL - UNITY 2D/3D - Conky 1.8.1)
#  Screen Resolution: 1280x1024x24 (DELL UltraSharp 1907FP)

####
## Prerequisites (required)
#
#  conky-all 1.8.0 or 1.8.1-5
#  cURL - Command Line Tool
#  xsltproc - Command Line Tool
#  UTF-8 Compatible Text Editor
#
## Tips n' Tricks
## Several ppl (including myself) have experienced issues with conky-all 1.8.1-6
## In every instance, downgrading to conky-all 1.8.1-5 has solved the problem(s).
## I recommend using (and pinning) conky-all 1.8.1-5 until things get sorted.
## conky-all 1.8.1-5 can be downloaded here: https://launchpad.net/ubuntu/+source/conky-all/1.8.1-5

####
## Installed fonts (required)
#
#  ConkyWeather (Stanko Metodiev)
#  Cut Outs for 3D FX (Fonts & Things)
#  Droid Font Family (Google Android SDK)
#  KR A Round (Kat's Fun Fonts)
#  OpenLogos (Icoma)
#  PizzaDude Bullets (Jakob Fischer)
#  Radio Space (Iconian Fonts)
#  StyleBats (Vinterstille)
#  Ubuntu Font Family (Canonical Ltd)
#  Ubuntu Title Bold (Paulo Silva - not included in link below)
#  Weather (Jonathan Macagba)
# 
## Tips n' Tricks from Mr. Peachy, djyoung4, and 42dorian (Thanks!)
## Most necessary fonts can be downloaded here: http://ompldr.org/vOHdoag
## Unzip the fonts into your font folder, for example: /home/username/.fonts
## Run this command in a terminal (rebuilds font cache file): sudo fc-cache -fv

####
## Use XFT? Required to Force UTF8 (see below)
#
use_xft yes
xftfont DroidSans:size=8.75
xftalpha 0.1

####
## Force UTF8? Requires XFT (see above)
## Displays degree symbol, instead of Â°, etc.
#
override_utf8_locale yes

####
## This buffer is used for text, single lines, output from $exec, and other variables.
## Increasing the text buffer size (too high) will drastically reduce Conky's performance.
## Decreasing the size (too low) will truncate content and cause strange display output.
## Standard text buffer size is 256 bytes (cannot be less). Adjust YOUR buffer wisely!
#
text_buffer_size 640

####
## Daemonize Conky, aka 'fork to background'.
#
background yes

####
## Update interval in seconds.
#
update_interval 2.0

####
## The number of times Conky will update before quitting.
## Zero makes Conky run forever.
#
total_run_times 0

####
## Create own window in instead of using desktop?
#
own_window yes
own_window_transparent yes
own_window_type normal
own_window_class conky-semi
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
####
## Some distros also require the following 2 lines.
#
own_window_argb_visual yes
own_window_argb_value 255

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
draw_shades yes
default_shade_color 292421

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
## Minimum size of the text area.
## Syntax: minimum_size [width] [height]
#
minimum_size 240 1394

####
## Maximum width of the text area.
## Syntax: maximum_width [width]
#
maximum_width 240

####
## Gap between text and screen borders.
#
gap_x 6	  ## Left / Right
gap_y 32  ## Top / Bottom

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
## My colors (suit yourself)
#
color0 White		#FFFFFF
color1 Ivory		#FFFFF0
color2 Ivory2		#EEEEE0
color3 Ivory3		#CDCDC1
color4 Tan1		#FFA54F
color5 Tan2		#EE9A49
color6 Gray		#7E7E7E
color7 AntiqueWhite4	#8B8378
color8 DimGray		#696969
color9 Tomato		#FF6347

#####
## Load Lua for shading (optional)
## Set the path to your script here.
#
lua_load ~/.conky/draw_bg.lua
lua_draw_hook_pre draw_bg

####
## Load Lua for bargraphs (required)
## Set the path to your script here.
#
lua_load ~/.conky/bargraph_small.lua
lua_draw_hook_post main_bars

TEXT
##################################
##             LOGO             ##
##################################
## Uncomment for hard-coded ID (static)
#${voffset -33}${font OpenLogos:size=103}${color2}v${font}${voffset -76}${goto 179}${font UbuntuTitleBold:size=19.6}${color4}1${offset 1}2${offset 1}.${offset 0}0${offset 0}4${font}
####
## Uncomment for soft-coded ID (dynamic)
${voffset -33}${font OpenLogos:size=103}${color2}v${font}${voffset -76}${goto 179}${font UbuntuTitleBold:size=19.6}${color4}${pre_exec cat /etc/*release | grep 'RELEASE' | awk -F'=' '{print $2}'}${font}
####
## Additional ID (branch version, code name, release date, etc.)
${voffset -1}${goto 188}${font Ubuntu-B:size=8.1}${color4}alpha 1${font}
##################################
##            SYSTEM            ##
##################################
${voffset 7}${font DroidSans:bold:size=8.25}${color4}SYSTEM${offset 8}${color8}${voffset -2}${hr 2}${font}
# ${voffset 4}${font OpenLogos:size=10}${color2}u${voffset -4}${font DroidSans:size=8.6}${color3}${offset 5}${pre_exec lsb_release -sd || cat /etc/*release}${font}
${voffset 2}${offset -2}${font OpenLogos:size=12}${color2}Z${voffset -4}${font DroidSans:size=8.6}${color3}${offset 3}${sysname}${offset 3}${kernel}${alignr}${font DroidSans:size=8.3}${machine}${font}
${voffset 2}${font StyleBats:size=10}${color2}d${voffset -2}${font DroidSans:size=8.6}${color3}${offset 5}ATI Radeon HD 4700${alignr}${font DroidSans:size=8.3}${pre_exec dpkg --status nvidia-current | grep Version | cut -f 1 -d '-' | sed 's/[^.,0-9]//g'}${font}
${voffset 2}${font StyleBats:size=10}${color2}A${voffset -1}${font DroidSans:size=8.6}${color3}${offset 5}Intel${offset 3}Core™2 Duo${offset 3}CPU${offset 3}E6850${alignr 1}${font DroidSans:size=8.3}${freq_g cpu0}${offset 1}GHz${font}
${voffset 2}${font StyleBats:size=10}${color2}q${voffset -1}${font DroidSans:size=8.6}${color3}${offset 5}System${offset 3}Uptime${alignr}${font DroidSans:size=8.3}${uptime_short}${font}
##################################
##          PROCESSORS          ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}PROCESSORS${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=9.9}${color2}k${voffset -2}${font DroidSansFallback:size=8.39}${color3}${offset 2}CPU1${offset 5}${font DroidSans:size=8.3}${cpu cpu1}%${font}
${voffset 2}${font StyleBats:size=9.9}${color2}k${voffset -2}${font DroidSansFallback:size=8.39}${color3}${offset 2}CPU2${offset 5}${font DroidSans:size=8.3}${cpu cpu2}%${font}
##################################
##            MEMORY            ##
##################################
${voffset 5}${font DroidSans:bold:size=8}${color4}MEMORY${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=10}${color2}l${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 3}RAM${goto 97}${font DroidSans:size=8.3}${mem}${goto 133}/${offset 5}${memmax}${alignr}${memperc}%${font}
##################################
##             HDD              ##
##################################
${voffset 15}${font DroidSans:bold:size=8}${color4}HDD${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 6}${font StyleBats:size=9.9}${color2}x${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}ROOT${goto 95}${font DroidSans:size=8.3}${fs_used /}${goto 133}/${offset 5}${fs_size /}${alignr}${fs_free_perc /}%${font}
${voffset 15}${font StyleBats:size=9.9}${color2}x${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}HOME${goto 95}${font DroidSans:size=8.3}${fs_used /home}${goto 133}/${offset 5}${fs_size /home}${alignr}${fs_free_perc /home}%${font}
${voffset 15}${font StyleBats:size=9.9}${color2}4${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}SWAP${goto 95}${font DroidSans:size=8.3}${swap}${goto 133}/${offset 5}${swapmax}${alignr}${swapperc}%${font}
##################################
##         TOP PROCESSES        ##
##################################
${voffset 15}${font DroidSans:bold:size=8}${color4}TOP PROCESSES${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 6}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 1}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 1}${alignr}${top_mem mem 1}%${font}
${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 2}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 2}${alignr}${top_mem mem 2}%${font}
${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 3}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 3}${alignr}${top_mem mem 3}%${font}
${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 4}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 4}${alignr}${top_mem mem 4}%${font}
${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 5}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 5}${alignr}${top_mem mem 5}%${font}
# ${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 6}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 6}${alignr}${top_mem mem 6}%${font}
##################################
##           NETWORK            ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}NETWORK${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font PizzaDudeBullets:size=9.5}${color6}T${font DroidSans:size=8.65}${color3}${offset 5}Download${goto 120}${font DroidSans:size=8.3}${totaldown wlan0}${alignr}${font DroidSans:size=8.3}${downspeed wlan0}${font}
${voffset 0}${font PizzaDudeBullets:size=9.5}${color6}N${font DroidSans:size=8.65}${color3}${offset 5}Upload${goto 120}${font DroidSans:size=8.3}${totalup wlan0}${alignr}${font DroidSans:size=8.3}${upspeed wlan0}${font}
#${voffset 4}${font PizzaDudeBullets:size=9.5}${color6}a${font DroidSans:size=8.65}${color3}${offset 5}Private${offset 3}IP${goto 123}#${font DroidSansFallback:size=8.5}LAN${alignr}${font DroidSans:size=8.3}${addr wlan0}${font}
#${voffset 0}${font PizzaDudeBullets:size=9.5}${color6}a${font DroidSans:size=8.65}${color3}${offset 5}Public${offset 7}IP${goto 121}#${font DroidSansFallback:size=8.5}WAN${alignr}${font DroidSans:size=8.3}${execi 1800 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}${font}
##################################
##     WEATHER (Imperial)       ##
##################################
#${voffset 4}${font DroidSans:bold:size=8.25}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
#${voffset -55}${font RadioSpace:size=34}${color3}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" ctbi}${font}${voffset -28}#${goto 33}${font Weather:size=42}${color3}y${font}
#${voffset -38}${font Ubuntu:size=8.63}${color5}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" ctti}${font}
#${voffset -39}${font KRARound:size=36}${color3}${goto 195}I${font}
#${voffset 6}${font Ubuntu:size=23}${color5}${alignc -2}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" ccb}${font}
#${voffset 8}${font DroidSansFallback:size=8.63}${color3}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ"}${font}
#${voffset -57}${font ConkyWeather:size=48}${color6}${alignc -55}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" cp}${font}
#${voffset 6}${font DroidSansMono:bold:size=8.62}${color4}${offset 40}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" dl}#${font}
#${voffset 0}${font ConkyWeather:size=37.9}${color3}${offset 26}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" fcp}${font}
#${voffset 0}${font DroidSansFallback:bold:size=8.62}${color4}${offset 28}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" fcti}${font}
##################################
##      WEATHER (Metric)        ##
##################################
${voffset 4}${font DroidSans:bold:size=8.25}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
 ${voffset -55}${font RadioSpace:size=34}${color3}${execi 1800 /home/jan/.conky/weather/weather.sh "Toronto" ctbm}${font}${voffset -28}${goto 33}${font Weather:size=42}${color3}y${font}
 ${voffset -38}${font Ubuntu:size=8.63}${color5}${execi 1800 /home/jan/.conky/weather/weather.sh "Toronto" cttm}${font}
 ${voffset -39}${font KRARound:size=36}${color3}${goto 195}I${font}
 ${voffset 6}${font Ubuntu:size=23}${color5}${alignc -2}${execi 1800 /home/jan/.conky/weather/weather.sh "Toronto" ccb}${font}
 ${voffset 8}${font DroidSansFallback:size=8.63}${color3}${execi 1800 /home/jan/.conky/weather/weather.sh "Toronto"}${font}
 ${voffset -57}${font ConkyWeather:size=48}${color6}${alignc -55}${execi 1800 /home/jan/.conky/weather/weather.sh "Toronto" cp}${font}
 ${voffset 6}${font DroidSansMono:bold:size=8.62}${color4}${offset 40}${execi 1800 /home/jan/.conky/weather/weather.sh "Toronto" dl}${font}
 ${voffset 0}${font ConkyWeather:size=37.9}${color3}${offset 26}${execi 1800 /home/jan/.conky/weather/weather.sh "Toronto" fcp}${font}
 ${voffset 0}${font DroidSansFallback:bold:size=8.62}${color4}${offset 35}${execi 1800 /home/jan/.conky/weather/weather.sh "Toronto" fctm}${font}
##################################
##             TIME             ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}TIME${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset -4}${font RadioSpace:size=32}${color3}${if_match ${time %l}<=9}${alignc 7}${time %l:%M%p}${else}${if_match ${time %l}>=10}${alignc -1}${time %l:%M%p}${endif}${endif}${font}
##################################
##      CALENDAR (5-Line)       ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}DATE${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 18}${font DroidSansMono:size=7.55}${color3}${alignc 60}${time %A}${font}
${voffset -4}${font DroidSansFallback:bold:size=18}${if_match ${time %e}<=9}${color5}${alignc 65}${time %e}${font}${else}${if_match ${time %e}>=10}${color5}${alignc 60}${time %e}${endif}${endif}${font}
${voffset 0}${font DroidSansMono:size=7.55}${color3}${alignc 60}${time %B}${font}
${voffset 0}${font DroidSansMono:size=7.6}${color3}${alignc 60}${time %Y}${font}
${voffset -83}${font CutOutsFor3DFX:size=67}${color8}${alignc 99}2${font}
####
## Uncomment for Conky 1.8.0 (use mono fonts only)
# ${voffset -68}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_9=`date +%-d`; ncal -M -C -h | sed -e 's/\r//g' -e 's/^/ /g' -e '1d' -e 's/\<'"$VinDSL_Cal_9"'\>/${color4}&${color3}/'}
####
## Uncomment for Conky 1.8.1 (use mono fonts only)
${voffset -64}${offset 100}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_9=`date +%-d`; ncal -M -C -h | sed -e 's/\r//g' -e 's/^/ /g' -e '1d' -e 's/\<'"$VinDSL_Cal_9"'\>/${color4}&${color3}/'}
##################################
##   RHYTHMBOX (Experimental)   ##
##################################
${if_running rhythmbox}
${voffset -8}${font DroidSans:bold:size=7.75}${color4}RHYTHMBOX${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 8}${font DroidSans:size=8.25}${color3}${if_match "${execpi 2 expr length "`/usr/bin/rhythmbox-client --print-playing-format %tt | head -n 1`"}" >= "48"}${alignr 15}${scroll 38 4* ${execi 2 rhythmbox-client --print-playing-format %tt --no-start}}${font}${else}${alignc}${execi 2 rhythmbox-client --print-playing-format %tt --no-start}${font}${endif}${endif}
```

Also take a look at the attachments.

Any help would be appreciated.

---

### Post by GreatDanton on 2012-07-04
bump

---

### Post by Gillingham on 2012-07-04
Ok you are getting:
> Package `nvidia-current' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents. 
is because of the line
> ${voffset 2}${font StyleBats:size=10}${color2}d${voffset -2}${font DroidSans:size=8.6}${color3}${offset 5}ATI Radeon HD 4700${alignr}${font DroidSans:size=8.3}${pre_exec dpkg --status nvidia-current | grep Version | cut -f 1 -d '-' | sed 's/[^.,0-9]//g'}${font}

in particular the part "${pre_exec dpkg --status nvidia-current" As you don't have nvidia-current installed you are getting the message when you start conky.  I would probably edit this line to read

```
${voffset 2}${font StyleBats:size=10}${color2}d${voffset -2}${font DroidSans:size=8.6}${color3}${offset 5}ATI Radeon HD 4700${font}
```

The error:
> /home/jan/.conky/weather/weather.sh: line 149: /usr/bin/curl: No such file or directory
/home/jan/.conky/weather/weather.sh: line 156: /usr/bin/xsltproc: No such file or directory

Are probably due to 2 programs (curl and xsltproc) not being installed on your system.  These 2 are used by the script to get the weather data from the web.  I recommend that you use the software centre to read about these commands and then install them.  This should get the weather bit working.

The auto detection is a bit more tricky

the alpha comes from the line
```
## Additional ID (branch version, code name, release date, etc.)
${voffset -1}${goto 188}${font Ubuntu-B:size=8.1}${color4}alpha 1${font}
```

I'd be tempted to delete or comment this out.

the version number is being got from these lines
```
## Uncomment for soft-coded ID (dynamic)
${voffset -33}${font OpenLogos:size=103}${color2}v${font}${voffset -76}${goto 179}${font UbuntuTitleBold:size=19.6}${color4}${pre_exec cat /etc/*release | grep 'RELEASE' | awk -F'=' '{print $2}'}${font}
```
 with the work being done by
```
cat /etc/*release | grep 'RELEASE' | awk -F'=' '{print $2}'
```
the pre_exec before this means execute once before conky starts which is correct as this won't change except after a system restart.  I suggest that you run this command and check that you get the correct answer (I did so I assume the syntax is correct).  If this does give you the right answer, then probably the "4" is being lost outside of the conky window and you have several choices: reduce the font size somewhere in the line or increase the width of the window by editing the line
```
####
## Maximum width of the text area.
## Syntax: maximum_width [width]
#
maximum_width 240
```

I think both will work but go with which ever looks better to you.


I hope you will be able to follow this reply.

---

### Post by GreatDanton on 2012-07-04
Thank you very much Gillingham. I will start to correct this things right away. Very nice tutorial.

Thank you one more time.

---

### Post by GreatDanton on 2012-07-04
Here is the update: I made like you suggested, and there is no more errors. You can see my conky in the attachments.

Few more problems remain:
Edit: The location now changed to the right one.

Also I would like to move Calendar to the right (so the numbers will be at the right days), and temperature down a little bit (because I can't see network :D).Is this possible?

Thank you.

P.S here is the current version of Conky script-if anyone is interested.
```
# Conky, a system monitor, based on torsmo
#
# Any original torsmo code is licensed under the BSD license
#
# All code written since the fork of torsmo is licensed under the GPL
#
# Please see COPYING for details
#
# Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
# Copyright (c) 2005-2010 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
# All rights reserved.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

# Conky configuration
alignment top_right
background yes
##################################
## VinDSL | rev. 11-12-01 20:20 ##
##################################
##     December 2011 Series     ##
##################################

## ¡PLEASE READ THE FINE PRINT! ##

####
## Development Platforms (current)
#
#  Ubuntu 10.10 'Maverick Meerkat' (GNOME 2.28 - Conky 1.8.0)
#  Ubuntu 12.04 'Precise Pangolin' (GNOME-SHELL - UNITY 2D/3D - Conky 1.8.1)
#  Screen Resolution: 1280x1024x24 (DELL UltraSharp 1907FP)

####
## Prerequisites (required)
#
#  conky-all 1.8.0 or 1.8.1-5
#  cURL - Command Line Tool
#  xsltproc - Command Line Tool
#  UTF-8 Compatible Text Editor
#
## Tips n' Tricks
## Several ppl (including myself) have experienced issues with conky-all 1.8.1-6
## In every instance, downgrading to conky-all 1.8.1-5 has solved the problem(s).
## I recommend using (and pinning) conky-all 1.8.1-5 until things get sorted.
## conky-all 1.8.1-5 can be downloaded here: https://launchpad.net/ubuntu/+source/conky-all/1.8.1-5

####
## Installed fonts (required)
#
#  ConkyWeather (Stanko Metodiev)
#  Cut Outs for 3D FX (Fonts & Things)
#  Droid Font Family (Google Android SDK)
#  KR A Round (Kat's Fun Fonts)
#  OpenLogos (Icoma)
#  PizzaDude Bullets (Jakob Fischer)
#  Radio Space (Iconian Fonts)
#  StyleBats (Vinterstille)
#  Ubuntu Font Family (Canonical Ltd)
#  Ubuntu Title Bold (Paulo Silva - not included in link below)
#  Weather (Jonathan Macagba)
# 
## Tips n' Tricks from Mr. Peachy, djyoung4, and 42dorian (Thanks!)
## Most necessary fonts can be downloaded here: http://ompldr.org/vOHdoag
## Unzip the fonts into your font folder, for example: /home/username/.fonts
## Run this command in a terminal (rebuilds font cache file): sudo fc-cache -fv

####
## Use XFT? Required to Force UTF8 (see below)
#
use_xft yes
xftfont DroidSans:size=8.75
xftalpha 0.1

####
## Force UTF8? Requires XFT (see above)
## Displays degree symbol, instead of Â°, etc.
#
override_utf8_locale yes

####
## This buffer is used for text, single lines, output from $exec, and other variables.
## Increasing the text buffer size (too high) will drastically reduce Conky's performance.
## Decreasing the size (too low) will truncate content and cause strange display output.
## Standard text buffer size is 256 bytes (cannot be less). Adjust YOUR buffer wisely!
#
text_buffer_size 640

####
## Daemonize Conky, aka 'fork to background'.
#
background yes

####
## Update interval in seconds.
#
update_interval 2.0

####
## The number of times Conky will update before quitting.
## Zero makes Conky run forever.
#
total_run_times 0

####
## Create own window in instead of using desktop?
#
own_window yes
own_window_transparent yes
own_window_type normal
own_window_class conky-semi
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
####
## Some distros also require the following 2 lines.
#
own_window_argb_visual yes
own_window_argb_value 255

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
draw_shades yes
default_shade_color 292421

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
## Minimum size of the text area.
## Syntax: minimum_size [width] [height]
#
minimum_size 240 1394

####
## Maximum width of the text area.
## Syntax: maximum_width [width]
#
maximum_width 255

####
## Gap between text and screen borders.
#
gap_x 6	  ## Left / Right
gap_y 32  ## Top / Bottom

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
## My colors (suit yourself)
#
color0 White		#FFFFFF
color1 Ivory		#FFFFF0
color2 Ivory2		#EEEEE0
color3 Ivory3		#CDCDC1
color4 Tan1		#FFA54F
color5 Tan2		#EE9A49
color6 Gray		#7E7E7E
color7 AntiqueWhite4	#8B8378
color8 DimGray		#696969
color9 Tomato		#FF6347

#####
## Load Lua for shading (optional)
## Set the path to your script here.
#
lua_load ~/.conky/draw_bg.lua
lua_draw_hook_pre draw_bg

####
## Load Lua for bargraphs (required)
## Set the path to your script here.
#
lua_load ~/.conky/bargraph_small.lua
lua_draw_hook_post main_bars

TEXT
##################################
##             LOGO             ##
##################################
## Uncomment for hard-coded ID (static)
#${voffset -33}${font OpenLogos:size=103}${color2}v${font}${voffset -76}${goto 179}${font UbuntuTitleBold:size=19.6}${color4}1${offset 1}2${offset 1}.${offset 0}0${offset 0}4${font}
####
## Uncomment for soft-coded ID (dynamic)
${voffset -33}${font OpenLogos:size=103}${color2}v${font}${voffset -76}${goto 179}${font UbuntuTitleBold:size=19.6}${color4}${pre_exec cat /etc/*release | grep 'RELEASE' | awk -F'=' '{print $2}'}${font}
####
## Additional ID (branch version, code name, release date, etc.)
${voffset -1}${goto 188}${font Ubuntu-B:size=7}${color4}Precise Pangolin${font}
##################################
##            SYSTEM            ##
##################################
${voffset 7}${font DroidSans:bold:size=8.25}${color4}SYSTEM${offset 8}${color8}${voffset -2}${hr 2}${font}
# ${voffset 4}${font OpenLogos:size=10}${color2}u${voffset -4}${font DroidSans:size=8.6}${color3}${offset 5}${pre_exec lsb_release -sd || cat /etc/*release}${font}
${voffset 2}${offset -2}${font OpenLogos:size=12}${color2}Z${voffset -4}${font DroidSans:size=8.6}${color3}${offset 3}${sysname}${offset 3}${kernel}${alignr}${font DroidSans:size=8.3}${machine}${font}
${voffset 2}${font StyleBats:size=10}${color2}d${voffset -2}${font DroidSans:size=8.6}${color3}${offset 5}ATI Radeon HD 4700${alignr}${font DroidSans:size=8.3}
${voffset 2}${font StyleBats:size=10}${color2}A${voffset -1}${font DroidSans:size=8.6}${color3}${offset 5}Intel${offset 3}Core&#8482;2 Duo${offset 3}CPU${offset 3}E6850${alignr 1}${font DroidSans:size=8.3}${freq_g cpu0}${offset 1}GHz${font}
${voffset 2}${font StyleBats:size=10}${color2}q${voffset -1}${font DroidSans:size=8.6}${color3}${offset 5}System${offset 3}Uptime${alignr}${font DroidSans:size=8.3}${uptime_short}${font}
##################################
##          PROCESSORS          ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}PROCESSORS${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=9.9}${color2}k${voffset -2}${font DroidSansFallback:size=8.39}${color3}${offset 2}CPU1${offset 5}${font DroidSans:size=8.3}${cpu cpu1}%${font}
${voffset 2}${font StyleBats:size=9.9}${color2}k${voffset -2}${font DroidSansFallback:size=8.39}${color3}${offset 2}CPU2${offset 5}${font DroidSans:size=8.3}${cpu cpu2}%${font}
##################################
##            MEMORY            ##
##################################
${voffset 5}${font DroidSans:bold:size=8}${color4}MEMORY${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=10}${color2}l${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 3}RAM${goto 97}${font DroidSans:size=8.3}${mem}${goto 133}/${offset 5}${memmax}${alignr}${memperc}%${font}
##################################
##             HDD              ##
##################################
${voffset 15}${font DroidSans:bold:size=8}${color4}HDD${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 6}${font StyleBats:size=9.9}${color2}x${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}ROOT${goto 95}${font DroidSans:size=8.3}${fs_used /}${goto 133}/${offset 5}${fs_size /}${alignr}${fs_free_perc /}%${font}
${voffset 15}${font StyleBats:size=9.9}${color2}x${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}HOME${goto 95}${font DroidSans:size=8.3}${fs_used /home}${goto 133}/${offset 5}${fs_size /home}${alignr}${fs_free_perc /home}%${font}
${voffset 15}${font StyleBats:size=9.9}${color2}4${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}SWAP${goto 95}${font DroidSans:size=8.3}${swap}${goto 133}/${offset 5}${swapmax}${alignr}${swapperc}%${font}
##################################
##         TOP PROCESSES        ##
##################################
${voffset 15}${font DroidSans:bold:size=8}${color4}TOP PROCESSES${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 6}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 1}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 1}${alignr}${top_mem mem 1}%${font}
${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 2}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 2}${alignr}${top_mem mem 2}%${font}
${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 3}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 3}${alignr}${top_mem mem 3}%${font}
${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 4}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 4}${alignr}${top_mem mem 4}%${font}
${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 5}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 5}${alignr}${top_mem mem 5}%${font}
# ${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 6}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 6}${alignr}${top_mem mem 6}%${font}
##################################
##           NETWORK            ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}NETWORK${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font PizzaDudeBullets:size=9.5}${color6}T${font DroidSans:size=8.65}${color3}${offset 5}Download${goto 120}${font DroidSans:size=8.3}${totaldown wlan0}${alignr}${font DroidSans:size=8.3}${downspeed wlan0}${font}
${voffset 0}${font PizzaDudeBullets:size=9.5}${color6}N${font DroidSans:size=8.65}${color3}${offset 5}Upload${goto 120}${font DroidSans:size=8.3}${totalup wlan0}${alignr}${font DroidSans:size=8.3}${upspeed wlan0}${font}
#${voffset 4}${font PizzaDudeBullets:size=9.5}${color6}a${font DroidSans:size=8.65}${color3}${offset 5}Private${offset 3}IP${goto 123}#${font DroidSansFallback:size=8.5}LAN${alignr}${font DroidSans:size=8.3}${addr wlan0}${font}
#${voffset 0}${font PizzaDudeBullets:size=9.5}${color6}a${font DroidSans:size=8.65}${color3}${offset 5}Public${offset 7}IP${goto 121}#${font DroidSansFallback:size=8.5}WAN${alignr}${font DroidSans:size=8.3}${execi 1800 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}${font}
##################################
##     WEATHER (Imperial)       ##
##################################
#${voffset 4}${font DroidSans:bold:size=8.25}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
#${voffset -55}${font RadioSpace:size=34}${color3}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" ctbi}${font}${voffset -28}#${goto 33}${font Weather:size=42}${color3}y${font}
#${voffset -38}${font Ubuntu:size=8.63}${color5}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" ctti}${font}
#${voffset -39}${font KRARound:size=36}${color3}${goto 195}I${font}
#${voffset 6}${font Ubuntu:size=23}${color5}${alignc -2}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" ccb}${font}
#${voffset 8}${font DroidSansFallback:size=8.63}${color3}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ"}${font}
#${voffset -57}${font ConkyWeather:size=48}${color6}${alignc -55}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" cp}${font}
#${voffset 6}${font DroidSansMono:bold:size=8.62}${color4}${offset 40}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" dl}#${font}
#${voffset 0}${font ConkyWeather:size=37.9}${color3}${offset 26}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" fcp}${font}
#${voffset 0}${font DroidSansFallback:bold:size=8.62}${color4}${offset 28}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" fcti}${font}
##################################
##      WEATHER (Metric)        ##
##################################
${voffset 4}${font DroidSans:bold:size=8.25}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
 ${voffset -55}${font RadioSpace:size=34}${color3}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" ctbm}${font}${voffset -28}${goto 33}${font Weather:size=42}${color3}y${font}
 ${voffset -38}${font Ubuntu:size=8.63}${color5}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" cttm}${font}
 ${voffset -39}${font KRARound:size=36}${color3}${goto 195}I${font}
 ${voffset 6}${font Ubuntu:size=23}${color5}${alignc -2}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" ccb}${font}
 ${voffset 8}${font DroidSansFallback:size=8.63}${color3}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana"}${font}
 ${voffset -57}${font ConkyWeather:size=48}${color6}${alignc -55}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" cp}${font}
 ${voffset 6}${font DroidSansMono:bold:size=8.62}${color4}${offset 40}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" dl}${font}
 ${voffset 0}${font ConkyWeather:size=37.9}${color3}${offset 26}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" fcp}${font}
 ${voffset 0}${font DroidSansFallback:bold:size=8.62}${color4}${offset 35}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" fctm}${font}
##################################
##             TIME             ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}TIME${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset -4}${font RadioSpace:size=32}${color3}${if_match ${time %l}<=9}${alignc 7}${time %l:%M%p}${else}${if_match ${time %l}>=10}${alignc -1}${time %l:%M%p}${endif}${endif}${font}
##################################
##      CALENDAR (5-Line)       ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}DATE${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 18}${font DroidSansMono:size=7.55}${color3}${alignc 60}${time %A}${font}
${voffset -4}${font DroidSansFallback:bold:size=18}${if_match ${time %e}<=9}${color5}${alignc 65}${time %e}${font}${else}${if_match ${time %e}>=10}${color5}${alignc 60}${time %e}${endif}${endif}${font}
${voffset 0}${font DroidSansMono:size=7.55}${color3}${alignc 60}${time %B}${font}
${voffset 0}${font DroidSansMono:size=7.6}${color3}${alignc 60}${time %Y}${font}
${voffset -83}${font CutOutsFor3DFX:size=67}${color8}${alignc 99}2${font}
####
## Uncomment for Conky 1.8.0 (use mono fonts only)
# ${voffset -68}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_9=`date +%-d`; ncal -M -C -h | sed -e 's/\r//g' -e 's/^/ /g' -e '1d' -e 's/\<'"$VinDSL_Cal_9"'\>/${color4}&${color3}/'}
####
## Uncomment for Conky 1.8.1 (use mono fonts only)
${voffset -64}${offset 100}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_9=`date +%-d`; ncal -M -C -h | sed -e 's/\r//g' -e 's/^/ /g' -e '1d' -e 's/\<'"$VinDSL_Cal_9"'\>/${color4}&${color3}/'}
##################################
##   RHYTHMBOX (Experimental)   ##
##################################
${if_running rhythmbox}
${voffset -8}${font DroidSans:bold:size=7.75}${color4}RHYTHMBOX${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 8}${font DroidSans:size=8.25}${color3}${if_match "${execpi 2 expr length "`/usr/bin/rhythmbox-client --print-playing-format %tt | head -n 1`"}" >= "48"}${alignr 15}${scroll 38 4* ${execi 2 rhythmbox-client --print-playing-format %tt --no-start}}${font}${else}${alignc}${execi 2 rhythmbox-client --print-playing-format %tt --no-start}${font}${endif}${endif}
```

---

### Post by Quarkrad on 2012-07-05
I've only just started playing with conky and too started with VinDSL's script.  As a newbie I can't help with the first part of your question but perhaps with the last bit - the calendar.  Pic1 shows what I had - although like you - originally the days of the week were on the right, not to left as mine shows.  The code that gave me this, in the Calendar part of conkyrc is:

**${voffset -64}${offset 0}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_9=`date +%-d`; cal -h | sed -e 's/\r//g' -e 's/^//g' -e '1d' -e 's/\<'"$VinDSL_Cal_9"'\>/${color4}&${color3}/'}**

you should have this in your script.

Pic2 shows what happens after I amended the script, the days of the week and the numbers moved to the right.  This is my amended script:

**${voffset -64}${offset 0}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_9=`date +%-d`; cal -h | sed -e 's/\r//g' -e 's/^/                   /g' -e '1d' -e 's/\<'"$VinDSL_Cal_9"'\>/${color4}&${color3}/'}**

As you see I put spaces (space bar) between **s/^/** and **/g' -e** in that part of the script.

A good resource/forum to get help with conky is [http://crunchbanglinux.org/forums/post/232005/#p232005](http://crunchbanglinux.org/forums/post/232005/#p232005)

---

### Post by Quarkrad on 2012-07-05
Ah, the spaces didn't show in the script when I copied it across (don't know why).  Look at pic3 - it showsthe amended script.

---

### Post by GreatDanton on 2012-07-05
Thank you very much. I will change that as soon as possible.

Now there is one more problem, I would like to bring temperatures down, and after that change the pictures of the weather (in my case there are letters).

Thanks.

---

### Post by Habitual on 2012-07-05
> **greatdanton said:**
> ...very nice tutorial....

+1

---

### Post by GreatDanton on 2012-07-05
Now different problem occurred. I put spaces like you suggested now the days gone into the right (take a look at the picture). Why this works for you, but not for me ??

Thanks.

---

### Post by GreatDanton on 2012-07-05
Oh, I forgot to post my conky. So here is the picture

---

### Post by Quarkrad on 2012-07-05
I haven't got a solution but this is what I did/am doing.  Make a copy of your conkyrc file so you have a good copy and then start playing with each line and then element in each line and see what happens.  You can put a # character at the start of a line to effectively blank that line out.  Start doing this and see what effect it has.  Playing about with each line lead me to moving the dates to the right and days of the week to the left.  You will soon find out what line and elements control the days of the week and how to move them.  One thing I have picked up is that the conky window will change as soon as you save the conkyrc file so you can see what effect a change has had.  But sometimes you also need, as well as, to restart conky to see the full effect.  You can put something like **killall conky** in terminal or make a script file on your Desktop to make the process easier.  I've been playing with this (VinDSL) script and trying to figure it all out - now, after a few weeks, I'm going to try and build my own to really learn how it all fits together and what does what.

---

### Post by GreatDanton on 2012-07-05
I have been playing with the conky file, and I wasn't able to move days to the left, however I was able to get the pictures of the weather. So here is my update :)

---

### Post by Quarkrad on 2012-07-06
Don't frget you will get some amazing support for conky at [http://crunchbanglinux.org/forums/topic/16909/the-new-monster-conky-thread/](http://crunchbanglinux.org/forums/topic/16909/the-new-monster-conky-thread/)

---

### Post by GreatDanton on 2012-07-06
Thank you. Wow it's amazing 2025 pages about conky.

---

### Post by GreatDanton on 2012-07-06
Here is the update: I made also the temperature section, but I don't know how to align temperatures (to be in the same column).

The other problems remains:
dates are on the right side
temperature is not at the right place

See attachments.

Here is the conky script:
```
# Conky, a system monitor, based on torsmo
#
# Any original torsmo code is licensed under the BSD license
#
# All code written since the fork of torsmo is licensed under the GPL
#
# Please see COPYING for details
#
# Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
# Copyright (c) 2005-2010 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
# All rights reserved.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

# Conky configuration
alignment top_right
background yes
##################################
## VinDSL | rev. 11-12-01 20:20 ##
##################################
##     December 2011 Series     ##
##################################

## ¡PLEASE READ THE FINE PRINT! ##

####
## Development Platforms (current)
#
#  Ubuntu 10.10 'Maverick Meerkat' (GNOME 2.28 - Conky 1.8.0)
#  Ubuntu 12.04 'Precise Pangolin' (GNOME-SHELL - UNITY 2D/3D - Conky 1.8.1)
#  Screen Resolution: 1280x1024x24 (DELL UltraSharp 1907FP)

####
## Prerequisites (required)
#
#  conky-all 1.8.0 or 1.8.1-5
#  cURL - Command Line Tool
#  xsltproc - Command Line Tool
#  UTF-8 Compatible Text Editor
#
## Tips n' Tricks
## Several ppl (including myself) have experienced issues with conky-all 1.8.1-6
## In every instance, downgrading to conky-all 1.8.1-5 has solved the problem(s).
## I recommend using (and pinning) conky-all 1.8.1-5 until things get sorted.
## conky-all 1.8.1-5 can be downloaded here: https://launchpad.net/ubuntu/+source/conky-all/1.8.1-5

####
## Installed fonts (required)
#
#  ConkyWeather (Stanko Metodiev)
#  Cut Outs for 3D FX (Fonts & Things)
#  Droid Font Family (Google Android SDK)
#  KR A Round (Kat's Fun Fonts)
#  OpenLogos (Icoma)
#  PizzaDude Bullets (Jakob Fischer)
#  Radio Space (Iconian Fonts)
#  StyleBats (Vinterstille)
#  Ubuntu Font Family (Canonical Ltd)
#  Ubuntu Title Bold (Paulo Silva - not included in link below)
#  Weather (Jonathan Macagba)
# 
## Tips n' Tricks from Mr. Peachy, djyoung4, and 42dorian (Thanks!)
## Most necessary fonts can be downloaded here: http://ompldr.org/vOHdoag
## Unzip the fonts into your font folder, for example: /home/username/.fonts
## Run this command in a terminal (rebuilds font cache file): sudo fc-cache -fv

####
## Use XFT? Required to Force UTF8 (see below)
#
use_xft yes
xftfont DroidSans:size=8.75
xftalpha 0.1

####
## Force UTF8? Requires XFT (see above)
## Displays degree symbol, instead of Â°, etc.
#
override_utf8_locale yes

####
## This buffer is used for text, single lines, output from $exec, and other variables.
## Increasing the text buffer size (too high) will drastically reduce Conky's performance.
## Decreasing the size (too low) will truncate content and cause strange display output.
## Standard text buffer size is 256 bytes (cannot be less). Adjust YOUR buffer wisely!
#
text_buffer_size 640

####
## Daemonize Conky, aka 'fork to background'.
#
background yes

####
## Update interval in seconds.
#
update_interval 2.0

####
## The number of times Conky will update before quitting.
## Zero makes Conky run forever.
#
total_run_times 0

####
## Create own window in instead of using desktop?
#
own_window yes
own_window_transparent yes
own_window_type normal
own_window_class conky-semi
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
####
## Some distros also require the following 2 lines.
#
own_window_argb_visual yes
own_window_argb_value 255

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
draw_shades yes
default_shade_color 292421

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
## Minimum size of the text area.
## Syntax: minimum_size [width] [height]
#
minimum_size 240 1394

####
## Maximum width of the text area.
## Syntax: maximum_width [width]
#
maximum_width 255

####
## Gap between text and screen borders.
#
gap_x 6	  ## Left / Right
gap_y 32  ## Top / Bottom

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
## My colors (suit yourself)
#
color0 White		#FFFFFF
color1 Ivory		#FFFFF0
color2 Ivory2		#EEEEE0
color3 Ivory3		#CDCDC1
color4 Tan1		#FFA54F
color5 Tan2		#EE9A49
color6 Gray		#7E7E7E
color7 AntiqueWhite4	#8B8378
color8 DimGray		#696969
color9 Tomato		#FF6347

#####
## Load Lua for shading (optional)
## Set the path to your script here.
#
lua_load ~/.conky/draw_bg.lua
lua_draw_hook_pre draw_bg

####
## Load Lua for bargraphs (required)
## Set the path to your script here.
#
lua_load ~/.conky/bargraph_small.lua
lua_draw_hook_post main_bars

TEXT
##################################
##             LOGO             ##
##################################
## Uncomment for hard-coded ID (static)
#${voffset -33}${font OpenLogos:size=103}${color2}v${font}${voffset -76}${goto 179}${font UbuntuTitleBold:size=19.6}${color4}1${offset 1}2${offset 1}.${offset 0}0${offset 0}4${font}
####
## Uncomment for soft-coded ID (dynamic)
${voffset -33}${font OpenLogos:size=103}${color2}v${font}${voffset -76}${goto 179}${font UbuntuTitleBold:size=19.6}${color4}${pre_exec cat /etc/*release | grep 'RELEASE' | awk -F'=' '{print $2}'}${font}
####
## Additional ID (branch version, code name, release date, etc.)
${voffset -1}${goto 188}${font Ubuntu-B:size=7}${color4}Precise Pangolin${font}
##################################
##            SYSTEM            ##
##################################
${voffset 7}${font DroidSans:bold:size=8.25}${color4}SYSTEM${offset 8}${color8}${voffset -2}${hr 2}${font}
# ${voffset 4}${font OpenLogos:size=10}${color2}u${voffset -4}${font DroidSans:size=8.6}${color3}${offset 5}${pre_exec lsb_release -sd || cat /etc/*release}${font}
${voffset 2}${offset -2}${font OpenLogos:size=12}${color2}Z${voffset -4}${font DroidSans:size=8.6}${color3}${offset 3}${sysname}${offset 3}${kernel}${alignr}${font DroidSans:size=8.3}${machine}${font}
${voffset 2}${font StyleBats:size=10}${color2}d${voffset -2}${font DroidSans:size=8.6}${color3}${offset 5}ATI Radeon HD 4800${alignr}${font DroidSans:size=8.3}
${voffset 2}${font StyleBats:size=10}${color2}A${voffset -1}${font DroidSans:size=8.6}${color3}${offset 5}Intel${offset 3}Core™2 Duo${offset 3}CPU${offset 3}E6850${alignr 1}${font DroidSans:size=8.3}${freq_g cpu0}${offset 1}GHz${font}
${voffset 2}${font StyleBats:size=10}${color2}q${voffset -1}${font DroidSans:size=8.6}${color3}${offset 5}System${offset 3}Uptime${alignr}${font DroidSans:size=8.3}${uptime_short}${font}
##################################
##          PROCESSORS          ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}PROCESSORS${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=9.9}${color2}k${voffset -2}${font DroidSansFallback:size=8.39}${color3}${offset 2}CPU1${offset 5}${font DroidSans:size=8.3}${cpu cpu1}%${font}
${voffset 2}${font StyleBats:size=9.9}${color2}k${voffset -2}${font DroidSansFallback:size=8.39}${color3}${offset 2}CPU2${offset 5}${font DroidSans:size=8.3}${cpu cpu2}%${font}
##################################
##            MEMORY            ##
##################################
${voffset 5}${font DroidSans:bold:size=8}${color4}MEMORY${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=10}${color2}l${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 3}RAM${goto 97}${font DroidSans:size=8.3}${mem}${goto 133}/${offset 5}${memmax}${alignr}${memperc}%${font}
##################################
##             HDD              ##
##################################
${voffset 15}${font DroidSans:bold:size=8}${color4}HDD${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 6}${font StyleBats:size=9.9}${color2}x${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}ROOT${goto 95}${font DroidSans:size=8.3}${fs_used /}${goto 133}/${offset 5}${fs_size /}${alignr}${fs_free_perc /}%${font}
${voffset 15}${font StyleBats:size=9.9}${color2}x${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}HOME${goto 95}${font DroidSans:size=8.3}${fs_used /home}${goto 133}/${offset 5}${fs_size /home}${alignr}${fs_free_perc /home}%${font}
${voffset 15}${font StyleBats:size=9.9}${color2}4${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}SWAP${goto 95}${font DroidSans:size=8.3}${swap}${goto 133}/${offset 5}${swapmax}${alignr}${swapperc}%${font}

#######################
#    TEMPERATURE      #  by Great Danton
#######################

${font DroidSans:size=8:weight=bold}${color4}TEMPERATURE  ${color8}${hr 2}$color
${font DroidSans:size=8.65}${color3}${exec sensors | grep "CPU"}
${exec sensors | grep "MB"}
${font DroidSans:size=8.65}${color3}Graphic card${exec sensors | grep "temp1"}
##################################
##         TOP PROCESSES        ##
##################################
${voffset 15}${font DroidSans:bold:size=8}${color4}TOP PROCESSES${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 6}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 1}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 1}${alignr}${top_mem mem 1}%${font}
${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 2}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 2}${alignr}${top_mem mem 2}%${font}
${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 3}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 3}${alignr}${top_mem mem 3}%${font}
${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 4}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 4}${alignr}${top_mem mem 4}%${font}
${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 5}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 5}${alignr}${top_mem mem 5}%${font}
# ${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 6}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 6}${alignr}${top_mem mem 6}%${font}
##################################
##           NETWORK            ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}NETWORK${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font PizzaDudeBullets:size=9.5}${color6}T${font DroidSans:size=8.65}${color3}${offset 5}Download${goto 120}${font DroidSans:size=8.3}${totaldown wlan0}${alignr}${font DroidSans:size=8.3}${downspeed wlan0}${font}
${voffset 0}${font PizzaDudeBullets:size=9.5}${color6}N${font DroidSans:size=8.65}${color3}${offset 5}Upload${goto 120}${font DroidSans:size=8.3}${totalup wlan0}${alignr}${font DroidSans:size=8.3}${upspeed wlan0}${font}
#${voffset 4}${font PizzaDudeBullets:size=9.5}${color6}a${font DroidSans:size=8.65}${color3}${offset 5}Private${offset 3}IP${goto 123}#${font DroidSansFallback:size=8.5}LAN${alignr}${font DroidSans:size=8.3}${addr wlan0}${font}
#${voffset 0}${font PizzaDudeBullets:size=9.5}${color6}a${font DroidSans:size=8.65}${color3}${offset 5}Public${offset 7}IP${goto 121}#${font DroidSansFallback:size=8.5}WAN${alignr}${font DroidSans:size=8.3}${execi 1800 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}${font}
##################################
##     WEATHER (Imperial)       ##
##################################
#${voffset 4}${font DroidSans:bold:size=8.25}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
#${voffset -55}${font RadioSpace:size=34}${color3}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" ctbi}${font}${voffset -28}#${goto 33}${font Weather:size=42}${color3}y${font}
#${voffset -38}${font Ubuntu:size=8.63}${color5}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" ctti}${font}
#${voffset -39}${font KRARound:size=36}${color3}${goto 195}I${font}
#${voffset 6}${font Ubuntu:size=23}${color5}${alignc -2}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" ccb}${font}
#${voffset 8}${font DroidSansFallback:size=8.63}${color3}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ"}${font}
#${voffset -57}${font ConkyWeather:size=48}${color6}${alignc -55}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" cp}${font}
#${voffset 6}${font DroidSansMono:bold:size=8.62}${color4}${offset 40}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" dl}#${font}
#${voffset 0}${font ConkyWeather:size=37.9}${color3}${offset 26}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" fcp}${font}
#${voffset 0}${font DroidSansFallback:bold:size=8.62}${color4}${offset 28}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" fcti}${font}
##################################
##      WEATHER (Metric)        ##
##################################
${voffset 4}${font DroidSans:bold:size=8.25}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
 ${voffset -55}${font RadioSpace:size=34}${color3}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" ctbm}${font}${voffset -28}${goto 33}${font Weather:size=42}${color3}y${font}
 ${voffset -38}${font Ubuntu:size=8.63}${color5}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" cttm}${font}
 ${voffset -39}${font KRARound:size=36}${color3}${goto 195}I${font}
 ${voffset 6}${font Ubuntu:size=23}${color5}${alignc -2}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" ccb}${font}
 ${voffset 8}${font DroidSansFallback:size=8.63}${color3}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana"}${font}
 ${voffset -57}${font ConkyWeather:size=48}${color6}${alignc -55}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" cp}${font}
 ${voffset 6}${font DroidSansMono:bold:size=8.62}${color4}${offset 40}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" dl}${font}
 ${voffset 0}${font ConkyWeather:size=37.9}${color3}${offset 26}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" fcp}${font}
 ${voffset 0}${font DroidSansFallback:bold:size=8.62}${color4}${offset 35}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" fctm}${font}
##################################
##             TIME             ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}TIME${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset -4}${font RadioSpace:size=32}${color3}${if_match ${time %l}<=9}${alignc 7}${time %l:%M%p}${else}${if_match ${time %l}>=10}${alignc -1}${time %l:%M%p}${endif}${endif}${font}
##################################
##      CALENDAR (5-Line)       ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}DATE${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 18}${font DroidSansMono:size=7.55}${color3}${alignc 60}${time %A}${font}
${voffset -4}${font DroidSansFallback:bold:size=18}${if_match ${time %e}<=9}${color5}${alignc 65}${time %e}${font}${else}${if_match ${time %e}>=10}${color5}${alignc 60}${time %e}${endif}${endif}${font}
${voffset 0}${font DroidSansMono:size=7.55}${color3}${alignc 60}${time %B}${font}
${voffset 0}${font DroidSansMono:size=7.6}${color3}${alignc 60}${time %Y}${font}
${voffset -83}${font CutOutsFor3DFX:size=67}${color8}${alignc 99}2${font}
####
## Uncomment for Conky 1.8.0 (use mono fonts only)
# ${voffset -68}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_9=`date +%-d`; ncal -M -C -h | sed -e 's/\r//g' -e 's/^/ /g' -e '1d' -e 's/\<'"$VinDSL_Cal_9"'\>/${color4}&${color3}/'}
####
## Uncomment for Conky 1.8.1 (use mono fonts only)
${voffset -64}${offset 100}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_9=`date +%-d`; ncal -M -C -h | sed -e 's/\r//g' -e 's/^/                    /g' -e '1d' -e 's/\<'"$VinDSL_Cal_9"'\>/${color4}&${color3}/'}



##################################
##   RHYTHMBOX (Experimental)   ##
##################################
${if_running rhythmbox}
${voffset -8}${font DroidSans:bold:size=7.75}${color4}RHYTHMBOX${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 8}${font DroidSans:size=8.25}${color3}${if_match "${execpi 2 expr length "`/usr/bin/rhythmbox-client --print-playing-format %tt | head -n 1`"}" >= "48"}${alignr 15}${scroll 38 4* ${execi 2 rhythmbox-client --print-playing-format %tt --no-start}}${font}${else}${alignc}${execi 2 rhythmbox-client --print-playing-format %tt --no-start}${font}${endif}${endif}
```

---

### Post by Quackers on 2012-07-06
Hi GreatDanton can you just recap for me please? I've got mixed up reading the thread :-)
Please change your backgound to a plain one so the conky display can be more easily seen and post another screenshot then list exactly what you want to do with it please.
Thanks

---

### Post by GreatDanton on 2012-07-06
Here is the screenshot.

I would like to change:
1. The part where (SYSTEM) where is Intel core 2 Duo Cpu e6850. There is 2.00 GHz but I have 3.00 GHz. So how to change 2.00 ghz to 3.00 ghz

2. TEMPERATURE section: I want to align temperatures to be in the same column (at the end of the conky bar), not like it's now. Also I don't want to see this: (high =+60C, cri).  Also take a look at the last thing on list (Graphic card temp1). How can I remove this temp1.

3. NETWORK section: Temperature is at the network section. I want to bring it down, so I can clearly see temperatures and network section. At the right part of the screen is some kind of meter. Also I would like to bring it down.

4. WEATHER section: at the bottom of weather section you can see temperatures. The second and the third are not at the right place (too far to right).

5.DATE section:  The days of the week are to far away to the right. I want to bring it to the left.

I hope you will be able to follow this.

Thank you for your help

---

### Post by Quackers on 2012-07-06
1) cpu speed should be automatic afaik. Maybe your processor is actually running at 2.0GHz? Don't know how to change it.

2) We can come back to this one

3) In your conkyrc file go to this part ```
##################################
##      WEATHER (Metric)        ##
##################################
${voffset 4}${font DroidSans:bold:size=8.25}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
 ${voffset -55}${font RadioSpace:size=34}${color3}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" ctbm}${font}${voffset -28}${goto 33}${font Weather:size=42}${color3}y${font}
 ${voffset -38}${font Ubuntu:size=8.63}${color5}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" cttm}${font}
 ${voffset -39}${font KRARound:size=36}${color3}${goto 195}I${font}
 ${voffset 6}${font Ubuntu:size=23}${color5}${alignc -2}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" ccb}${font}
 ${voffset 8}${font DroidSansFallback:size=8.63}${color3}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana"}${font}
 ${voffset -57}${font ConkyWeather:size=48}${color6}${alignc -55}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" cp}${font}
 ${voffset 6}${font DroidSansMono:bold:size=8.62}${color4}${offset 40}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" dl}${font}
 ${voffset 0}${font ConkyWeather:size=37.9}${color3}${offset 26}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" fcp}${font}
 ${voffset 0}${font DroidSansFallback:bold:size=8.62}${color4}${offset 35}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" fctm}${font}
``` and at the start of the second line remove ${voffset -55} so that the next bit (${font RadioSpace:size=34}) becomes the start of the line.

On the third line remove ${voffset -38} from the start of the line so that the line then starts with ${font Ubuntu:size=8.63}

On the fourth line remove ${voffset -39} so that the start of the line becomes ${font KRARound:size=36}

And while you're there all the $ signs at the start of each line in that weather section should be directly under each other and at the start of the line.

When the changes are made simply save the file and conky should automatically restart. 
Your display should move the temps down. Try that first please.

---

### Post by GreatDanton on 2012-07-06
This is what happened:

---

### Post by Quackers on 2012-07-06
Ok. Piece by piece this is going to take a long time and we won't get much of it done tonight.
For the moment go to the second line of the Weather (metric) section again which now starts with ${font RadioSpace:size=34}
At the start of that line type in ${alignc} and save the file. conky should move the large temp to the middle of the line

---

### Post by GreatDanton on 2012-07-06
I have to admit: Much better than before :D

---

### Post by Quackers on 2012-07-06
Too far right. Go back to same line and replace ${alignc} with ${goto 90}
Then on the fourth line start it with ${voffset -39} 
Then save the file etc

---

### Post by GreatDanton on 2012-07-06
Better and better

Would you mind explaining what is:

voffset?

edit: goto-found that

which is for which movement?

---

### Post by Quackers on 2012-07-06
A bit better.
goto is an instruction to go to a specific horizontal position within the display.
voffset is a specific vertical postition in respect of the current line.
But it's not quite that simple I'm afraid. It can change.

Ok back to the 4th line again and towards the end where it says ${goto 195}I${font} change the 195 to 210
leaving the rest as is then save

---

### Post by GreatDanton on 2012-07-06
...

Do you need screenruler? I have this aplication installed.

It was 5th line ;).

---

### Post by Quackers on 2012-07-06
Ok back to the 4th line again just before ${goto 210}I${font} type in 
${voffset -28}
Then at the start of the 3rd line type in ${goto 215}
Then save

---

### Post by GreatDanton on 2012-07-06
..
Wow 200 post.

---

### Post by Quackers on 2012-07-06
oops! delete the ${goto 215} then on line 3
On line 4 change the ${voffset -28} to read -40
then save

---

### Post by GreatDanton on 2012-07-06
here it is

---

### Post by Quackers on 2012-07-06
On line 4 change the voffset -40  to -38 and change the goto 210 back to 195 for now. At least it should look better even if the spacing isn't quite right.

That should be enough for tonight. My eyes are starting to look like my avatar :-) It's almost 2 am here and need to sleep.

We can look into other changes tomorrow some time, though I only can change a couple more I think.

---

### Post by GreatDanton on 2012-07-06
Sure not problem. I am happy you helped me. Here is the final update for tonight. It's almost 3 at night here :D

---

### Post by Quackers on 2012-07-06
Looking better now :-).
Ok have a sleep and I will too. Good night!

---

### Post by GreatDanton on 2012-07-06
Good night. Yes it's perfect.

---

### Post by Quackers on 2012-07-06
Lol, it's better :-)

---

### Post by GreatDanton on 2012-07-07
Here is the update of my conky script:

```
# Conky, a system monitor, based on torsmo
#
# Any original torsmo code is licensed under the BSD license
#
# All code written since the fork of torsmo is licensed under the GPL
#
# Please see COPYING for details
#
# Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
# Copyright (c) 2005-2010 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
# All rights reserved.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

# Conky configuration
alignment top_right
background yes
##################################
## VinDSL | rev. 11-12-01 20:20 ##
##################################
##     December 2011 Series     ##
##################################

## ¡PLEASE READ THE FINE PRINT! ##

####
## Development Platforms (current)
#
#  Ubuntu 10.10 'Maverick Meerkat' (GNOME 2.28 - Conky 1.8.0)
#  Ubuntu 12.04 'Precise Pangolin' (GNOME-SHELL - UNITY 2D/3D - Conky 1.8.1)
#  Screen Resolution: 1280x1024x24 (DELL UltraSharp 1907FP)

####
## Prerequisites (required)
#
#  conky-all 1.8.0 or 1.8.1-5
#  cURL - Command Line Tool
#  xsltproc - Command Line Tool
#  UTF-8 Compatible Text Editor
#
## Tips n' Tricks
## Several ppl (including myself) have experienced issues with conky-all 1.8.1-6
## In every instance, downgrading to conky-all 1.8.1-5 has solved the problem(s).
## I recommend using (and pinning) conky-all 1.8.1-5 until things get sorted.
## conky-all 1.8.1-5 can be downloaded here: https://launchpad.net/ubuntu/+source/conky-all/1.8.1-5

####
## Installed fonts (required)
#
#  ConkyWeather (Stanko Metodiev)
#  Cut Outs for 3D FX (Fonts & Things)
#  Droid Font Family (Google Android SDK)
#  KR A Round (Kat's Fun Fonts)
#  OpenLogos (Icoma)
#  PizzaDude Bullets (Jakob Fischer)
#  Radio Space (Iconian Fonts)
#  StyleBats (Vinterstille)
#  Ubuntu Font Family (Canonical Ltd)
#  Ubuntu Title Bold (Paulo Silva - not included in link below)
#  Weather (Jonathan Macagba)
# 
## Tips n' Tricks from Mr. Peachy, djyoung4, and 42dorian (Thanks!)
## Most necessary fonts can be downloaded here: http://ompldr.org/vOHdoag
## Unzip the fonts into your font folder, for example: /home/username/.fonts
## Run this command in a terminal (rebuilds font cache file): sudo fc-cache -fv

####
## Use XFT? Required to Force UTF8 (see below)
#
use_xft yes
xftfont DroidSans:size=8.75
xftalpha 0.1

####
## Force UTF8? Requires XFT (see above)
## Displays degree symbol, instead of Â°, etc.
#
override_utf8_locale yes

####
## This buffer is used for text, single lines, output from $exec, and other variables.
## Increasing the text buffer size (too high) will drastically reduce Conky's performance.
## Decreasing the size (too low) will truncate content and cause strange display output.
## Standard text buffer size is 256 bytes (cannot be less). Adjust YOUR buffer wisely!
#
text_buffer_size 640

####
## Daemonize Conky, aka 'fork to background'.
#
background yes

####
## Update interval in seconds.
#
update_interval 2.0

####
## The number of times Conky will update before quitting.
## Zero makes Conky run forever.
#
total_run_times 0

####
## Create own window in instead of using desktop?
#
own_window yes
own_window_transparent yes
own_window_type normal
own_window_class conky-semi
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
####
## Some distros also require the following 2 lines.
#
own_window_argb_visual yes
own_window_argb_value 255

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
draw_shades yes
default_shade_color 292421

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
## Minimum size of the text area.
## Syntax: minimum_size [width] [height]
#
minimum_size 240 1394

####
## Maximum width of the text area.
## Syntax: maximum_width [width]
#
maximum_width 255

####
## Gap between text and screen borders.
#
gap_x 6	  ## Left / Right
gap_y 32  ## Top / Bottom

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
## My colors (suit yourself)
#
color0 White		#FFFFFF
color1 Ivory		#FFFFF0
color2 Ivory2		#EEEEE0
color3 Ivory3		#CDCDC1
color4 Tan1		#FFA54F
color5 Tan2		#EE9A49
color6 Gray		#7E7E7E
color7 AntiqueWhite4	#8B8378
color8 DimGray		#696969
color9 Tomato		#FF6347

#####
## Load Lua for shading (optional)
## Set the path to your script here.
#
lua_load ~/.conky/draw_bg.lua
lua_draw_hook_pre draw_bg

####
## Load Lua for bargraphs (required)
## Set the path to your script here.
#
lua_load ~/.conky/bargraph_small.lua
lua_draw_hook_post main_bars

TEXT
##################################
##             LOGO             ##
##################################
## Uncomment for hard-coded ID (static)
#${voffset -33}${font OpenLogos:size=103}${color2}v${font}${voffset -76}${goto 179}${font UbuntuTitleBold:size=19.6}${color4}1${offset 1}2${offset 1}.${offset 0}0${offset 0}4${font}
####
## Uncomment for soft-coded ID (dynamic)
${voffset -33}${font OpenLogos:size=103}${color2}v${font}${voffset -76}${goto 179}${font UbuntuTitleBold:size=19.6}${color4}${pre_exec cat /etc/*release | grep 'RELEASE' | awk -F'=' '{print $2}'}${font}
####
## Additional ID (branch version, code name, release date, etc.)
${voffset -1}${goto 188}${font Ubuntu-B:size=7}${color4}Precise Pangolin${font}
##################################
##            SYSTEM            ##
##################################
${voffset 7}${font DroidSans:bold:size=8.25}${color4}SYSTEM${offset 8}${color8}${voffset -2}${hr 2}${font}
# ${voffset 4}${font OpenLogos:size=10}${color2}u${voffset -4}${font DroidSans:size=8.6}${color3}${offset 5}${pre_exec lsb_release -sd || cat /etc/*release}${font}
${voffset 2}${offset -2}${font OpenLogos:size=12}${color2}Z${voffset -4}${font DroidSans:size=8.6}${color3}${offset 3}${sysname}${offset 3}${kernel}${alignr}${font DroidSans:size=8.3}${machine}${font}
${voffset 2}${font StyleBats:size=10}${color2}d${voffset -2}${font DroidSans:size=8.6}${color3}${offset 5}ATI Radeon HD 4800${alignr}${font DroidSans:size=8.3}
${voffset 2}${font StyleBats:size=10}${color2}A${voffset -1}${font DroidSans:size=8.6}${color3}${offset 5}Intel${offset 3}Core™2 Duo${offset 3}CPU${offset 3}E6850${alignr 1}${font DroidSans:size=8.3}${freq_g cpu0}${offset 1}GHz${font}
${voffset 2}${font StyleBats:size=10}${color2}q${voffset -1}${font DroidSans:size=8.6}${color3}${offset 5}System${offset 3}Uptime${alignr}${font DroidSans:size=8.3}${uptime_short}${font}
##################################
##          PROCESSORS          ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}PROCESSORS${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=9.9}${color2}k${voffset -2}${font DroidSansFallback:size=8.39}${color3}${offset 2}CPU1${offset 5}${font DroidSans:size=8.3}${cpu cpu1}%${font}
${voffset 2}${font StyleBats:size=9.9}${color2}k${voffset -2}${font DroidSansFallback:size=8.39}${color3}${offset 2}CPU2${offset 5}${font DroidSans:size=8.3}${cpu cpu2}%${font}
##################################
##            MEMORY            ##
##################################
${voffset 5}${font DroidSans:bold:size=8}${color4}MEMORY${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=10}${color2}l${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 3}RAM${goto 97}${font DroidSans:size=8.3}${mem}${goto 133}/${offset 5}${memmax}${alignr}${memperc}%${font}
##################################
##             HDD              ##
##################################
${voffset 15}${font DroidSans:bold:size=8}${color4}HDD${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 6}${font StyleBats:size=9.9}${color2}x${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}ROOT${goto 95}${font DroidSans:size=8.3}${fs_used /}${goto 133}/${offset 5}${fs_size /}${alignr}${fs_free_perc /}%${font}
${voffset 15}${font StyleBats:size=9.9}${color2}x${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}HOME${goto 95}${font DroidSans:size=8.3}${fs_used /home}${goto 133}/${offset 5}${fs_size /home}${alignr}${fs_free_perc /home}%${font}
${voffset 15}${font StyleBats:size=9.9}${color2}4${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}SWAP${goto 95}${font DroidSans:size=8.3}${swap}${goto 133}/${offset 5}${swapmax}${alignr}${swapperc}%${font}

#######################
#    TEMPERATURE      #  by Great Danton
#######################

${font DroidSans:size=8:weight=bold}${color4}TEMPERATURE  ${color8}${hr 2}$color
${font DroidSans:size=8.65}${color3}${exec sensors | grep "CPU"}
${exec sensors | grep "MB"}
${font DroidSans:size=8.65}${color3}Graphic card${exec sensors | grep "temp1"}
##################################
##         TOP PROCESSES        ##
##################################
${voffset 15}${font DroidSans:bold:size=8}${color4}TOP PROCESSES${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 6}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 1}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 1}${alignr}${top_mem mem 1}%${font}
${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 2}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 2}${alignr}${top_mem mem 2}%${font}
${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 3}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 3}${alignr}${top_mem mem 3}%${font}
${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 4}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 4}${alignr}${top_mem mem 4}%${font}
${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 5}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 5}${alignr}${top_mem mem 5}%${font}
# ${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 6}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 6}${alignr}${top_mem mem 6}%${font}
##################################
##           NETWORK            ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}NETWORK${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font PizzaDudeBullets:size=9.5}${color6}T${font DroidSans:size=8.65}${color3}${offset 5}Download${goto 120}${font DroidSans:size=8.3}${totaldown wlan0}${alignr}${font DroidSans:size=8.3}${downspeed wlan0}${font}
${voffset 0}${font PizzaDudeBullets:size=9.5}${color6}N${font DroidSans:size=8.65}${color3}${offset 5}Upload${goto 120}${font DroidSans:size=8.3}${totalup wlan0}${alignr}${font DroidSans:size=8.3}${upspeed wlan0}${font}
#${voffset 4}${font PizzaDudeBullets:size=9.5}${color6}a${font DroidSans:size=8.65}${color3}${offset 5}Private${offset 3}IP${goto 123}#${font DroidSansFallback:size=8.5}LAN${alignr}${font DroidSans:size=8.3}${addr wlan0}${font}
#${voffset 0}${font PizzaDudeBullets:size=9.5}${color6}a${font DroidSans:size=8.65}${color3}${offset 5}Public${offset 7}IP${goto 121}#${font DroidSansFallback:size=8.5}WAN${alignr}${font DroidSans:size=8.3}${execi 1800 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}${font}
##################################
##     WEATHER (Imperial)       ##
##################################
#${voffset 4}${font DroidSans:bold:size=8.25}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
#${voffset -55}${font RadioSpace:size=34}${color3}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" ctbi}${font}${voffset -28}#${goto 33}${font Weather:size=42}${color3}y${font}
#${voffset -38}${font Ubuntu:size=8.63}${color5}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" ctti}${font}
#${voffset -39}${font KRARound:size=36}${color3}${goto 195}I${font}
#${voffset 6}${font Ubuntu:size=23}${color5}${alignc -2}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" ccb}${font}
#${voffset 8}${font DroidSansFallback:size=8.63}${color3}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ"}${font}
#${voffset -57}${font ConkyWeather:size=48}${color6}${alignc -55}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" cp}${font}
#${voffset 6}${font DroidSansMono:bold:size=8.62}${color4}${offset 40}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" dl}#${font}
#${voffset 0}${font ConkyWeather:size=37.9}${color3}${offset 26}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" fcp}${font}
#${voffset 0}${font DroidSansFallback:bold:size=8.62}${color4}${offset 28}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" fcti}${font}
##################################
##      WEATHER (Metric)        ##
##################################
${voffset 4}${font DroidSans:bold:size=8.25}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
${goto 90}${font RadioSpace:size=34}${color3}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" ctbm}${font}${voffset -28}${goto 33}${font Weather:size=42}${color3}y${font}
${voffset -39}${font Ubuntu:size=8.63}${color5}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" cttm}${font}
${font KRARound:size=36}${color3}${voffset -38}${goto 195}I${font}
${voffset 6}${font Ubuntu:size=23}${color5}${alignc -2}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" ccb}${font}
${voffset 8}${font DroidSansFallback:size=8.63}${color3}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana"}${font}
${voffset -57}${font ConkyWeather:size=48}${color6}${alignc -55}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" cp}${font}
${voffset 6}${font DroidSansMono:bold:size=8.62}${color4}${offset 40}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" dl}${font}
${voffset 0}${font ConkyWeather:size=37.9}${color3}${offset 26}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" fcp}${font}
${voffset 0}${font DroidSansFallback:bold:size=8.62}${color4}${offset 35}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" fctm}${font}
##################################
##             TIME             ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}TIME${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset -4}${font RadioSpace:size=32}${color3}${if_match ${time %l}<=9}${alignc 7}${time %l:%M%p}${else}${if_match ${time %l}>=10}${alignc -1}${time %l:%M%p}${endif}${endif}${font}
##################################
##      CALENDAR (5-Line)       ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}DATE${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 18}${font DroidSansMono:size=7.55}${color3}${alignc 60}${time %A}${font}
${voffset -4}${font DroidSansFallback:bold:size=18}${if_match ${time %e}<=9}${color5}${alignc 65}${time %e}${font}${else}${if_match ${time %e}>=10}${color5}${alignc 60}${time %e}${endif}${endif}${font}
${voffset 0}${font DroidSansMono:size=7.55}${color3}${alignc 60}${time %B}${font}
${voffset 0}${font DroidSansMono:size=7.6}${color3}${alignc 60}${time %Y}${font}
${voffset -83}${font CutOutsFor3DFX:size=67}${color8}${alignc 99}2${font}
####
## Uncomment for Conky 1.8.0 (use mono fonts only)
# ${voffset -68}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_9=`date +%-d`; ncal -M -C -h | sed -e 's/\r//g' -e 's/^/ /g' -e '1d' -e 's/\<'"$VinDSL_Cal_9"'\>/${color4}&${color3}/'}
####
## Uncomment for Conky 1.8.1 (use mono fonts only)
${voffset -64}${offset 100}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_9=`date +%-d`; ncal -M -C -h | sed -e 's/\r//g' -e 's/^/                    /g' -e '1d' -e 's/\<'"$VinDSL_Cal_9"'\>/${color4}&${color3}/'}



##################################
##   RHYTHMBOX (Experimental)   ##
##################################
${if_running rhythmbox}
${voffset -8}${font DroidSans:bold:size=7.75}${color4}RHYTHMBOX${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 8}${font DroidSans:size=8.25}${color3}${if_match "${execpi 2 expr length "`/usr/bin/rhythmbox-client --print-playing-format %tt | head -n 1`"}" >= "48"}${alignr 15}${scroll 38 4* ${execi 2 rhythmbox-client --print-playing-format %tt --no-start}}${font}${else}${alignc}${execi 2 rhythmbox-client --print-playing-format %tt --no-start}${font}${endif}${endif}
```

---

### Post by GreatDanton on 2012-07-07
update: I deleted the gap, take a look at the picture

---

### Post by GreatDanton on 2012-07-07
Calendar section is done :D

This is the right code:
```
## Uncomment for Conky 1.8.1 (use mono fonts only)
${voffset -64}${offset 0}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_9=`date +%-d`; ncal -M -C -h | sed -e 's/\r//g' -e 's/^/                    /g' -e '1d' -e 's/\<'"$VinDSL_Cal_9"'\>/${color4}&${color3}/'}
```

---

### Post by Quackers on 2012-07-07
Excellent! :-) Well done GreatDanton!

---

### Post by GreatDanton on 2012-07-07
Experimenting is the key to success :)

Thank you.

---

### Post by Quackers on 2012-07-07
Here's my conkyrc and a screenshot for you to compare
```
##################################
## VinDSL | rev. 11-06-01 00:27 ##
##################################
##        May 2011 Series       ##
##################################

## ¡PLEASE READ THE FINE PRINT! ##

####
## Development Platforms (currently)
#
#  Ubuntu 10.10 'Maverick Meerkat' (GNOME2)
#  Ubuntu 11.10 'Oneiric Ocelot'   (UNITY)
#  Screen Resolution: 1280x1024    (DELL)

####
## Prerequisites (required)
#
#  conky-all 1.8.0 or 1.8.1
#  conkyForecast 2.16 or newer 
#  Weather.com XML Data Feed (XOAP)
#  UTF-8 Compatible Text Editor

####
## Installed fonts (required)
#
#  ConkyWeather (Stanko Metodiev)
#  ConkyWindNESW (Stanko Metodiev)
#  Cut Outs for 3D FX (Fonts & Things)
#  Droid Font Family (Google Android SDK)
#  KR A Round (Kat's Fun Fonts)
#  Moon Phases (Curtis Clark)
#  OpenLogos (Icoma)
#  PizzaDude Bullets (Jakob Fischer)
#  Radio Space (Iconian Fonts)
#  StyleBats (Vinterstille)
#  Ubuntu Font Family (Canonical Ltd)
#  Ubuntu Title Bold (Paulo Silva)
#  Weather (Jonathan Macagba)
# 
## Tips from Mr. Peachy, djyoung4, and 42dorian:
## Download ALL of the necessary fonts listed above.
## Unzip fonts to your font folder. Example: /home/username/.fonts
## Run this command in a terminal (rebuilds cache): sudo fc-cache -fv

####
## Use XFT? Required to Force UTF8 (see below)
#
use_xft yes
xftfont DroidSans:size=8.75
xftalpha 0.1

####
## Force UTF8? Requires XFT (see above)
## Displays degree symbol, instead of Â°, etc.
#
override_utf8_locale yes

####
## This buffer is used for text, single lines, output from $exec, and other variables.
## Increasing the text buffer size (too high) will drastically reduce Conky's performance.
## Decreasing the size (too low) will truncate content and cause strange display output.
## Standard text buffer size is 256 bytes (cannot be less). Adjust YOUR buffer wisely!
#
text_buffer_size 1024

####
## Daemonize Conky, aka 'fork to background'.
#
background yes

####
## Update interval in seconds.
#
update_interval 1.5

####
## The number of times Conky will update before quitting.
## Zero makes Conky run forever.
#
total_run_times 0

####
## Create own window instead of using desktop?
#
own_window yes
own_window_transparent yes
own_window_argb_visual yes
own_window_type normal
own_window_class conky-semi
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

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
minimum_size 305 0
maximum_width 305

####
## Gap between text and screen borders.
#
gap_x 6	  ## Left / Right
gap_y 32  ## Top / Bottom

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
## My colors (suit yourself)
#
color0 White		#FFFFFF
color1 white #Ivory		#FFFFF0
color2 white #Ivory2		#EEEEE0
color3 white #Ivory3		#CDCDC1
color4 orange		#FFA54F
color5 Tan2		#EE9A49
color6 Gray		#7E7E7E
color7 AntiqueWhite4	#8B8378
color8 DimGray		#696969
color9 Black		#000000

#####
## Load Lua for shading (optional)
## Set the path to your script here.
#
#lua_load ~/.conky/draw_bg.lua
#lua_draw_hook_pre draw_bg

####
## Load Lua for bargraphs (required)
## Set the path to your script here.
#
lua_load ~/.conky/bargraph_small.lua
lua_draw_hook_post main_bars

TEXT
##################################
##             LOGO             ##
##################################
${color white}${offset 5}${voffset -40}${font OpenLogos:size=120}v${font}$alignr ${voffset -90}${goto 210}${color4}${font UbuntuTitleBold:style=bold:size=22}${pre_exec cat /etc/*release | grep 'RELEASE' | awk -F'=' '{print $2}'}${font}
##################################
##            SYSTEM            ##
##################################
${voffset 25}${font DroidSans:bold:size=12}${color4}SYSTEM${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 5}${offset -2}${font OpenLogos:size=14}${color2}Z${voffset -4}${font DroidSans:size=12}${color3}${offset 4}${sysname}${offset 5}${kernel}${alignr}${font DroidSans:size=12}${machine}${font}
${voffset 2}${font StyleBats:size=14}${color2}q${voffset -1}${font DroidSans:size=12}${color3}${offset 5}System${offset 3}Uptime${alignr}${font DroidSans:size=12}${uptime_short}${font}
##################################
##          PROCESSORS          ##
##################################
${voffset 6}${font DroidSans:bold:size=12}${color4}PROCESSORS${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 8}${font StyleBats:size=12}${color2}k${voffset -4}${font DroidSansFallback:size=12}${color3}${offset 2}CPU1${offset 5}${font DroidSans:size=12}${cpu cpu1}%${font}
${voffset 2}${font StyleBats:size=12}${color2}k${voffset -4}${font DroidSansFallback:size=12}${color3}${offset 2}CPU2${offset 5}${font DroidSans:size=12}${cpu cpu2}%${font}
##################################
##            MEMORY            ##
##################################
${voffset 6}${font DroidSans:bold:size=12}${color4}MEMORY${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 5}${font StyleBats:size=12}${color2}l${voffset -2}${font DroidSansFallback:size=12}${color3}${offset 3}RAM${goto 110}${font DroidSans:size=12}${mem}${goto 150}/${offset 5}${memmax}${alignr}${memperc}%${font}

##################################
##             HDD              ##
##################################
${voffset 6}${font DroidSans:bold:size=12}${color4}HDD${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 6}${font StyleBats:size=12}${color2}x${voffset -4}${font DroidSansFallback:size=12}${color3}${offset 4}ROOT${goto 110}${font DroidSans:size=12}${fs_used /}${goto 150}/${offset 5}${fs_size /}${alignr}${fs_used_perc /}%${font}

${voffset 15}${font StyleBats:size=12}${color2}x${voffset -4}${font DroidSansFallback:size=12}${color3}${offset 4}HOME${goto 110}${font DroidSans:size=12}${fs_used /home}${goto 150}/${offset 5}${fs_size /home}${alignr}${fs_used_perc /home}%${font}

##################################
##           BATTERY            ##
##################################
${voffset 10}${font DroidSans:bold:size=12}${color4}BATTERY${offset 8}${color8}${voffset -2}${hr 2}
${voffset -6}${font DroidSansFallback:size=12}${color1}${alignc}${battery BAT0}
##################################
##         TOP PROCESSES        ##
##################################

${voffset 4}${font DroidSans:bold:size=12}${color4}TOP PROCESSES${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=12}${color1}h${voffset -3}${font DroidSans:size=12}${color3}${offset 5}${top_mem name 1}${goto 150}${font DroidSans:size=12}${top_mem mem_res 1}${alignr}${top cpu 1}%${font}
${voffset 2}${font StyleBats:size=12}${color1}h${voffset -3}${font DroidSans:size=12}${color3}${offset 5}${top_mem name 2}${goto 150}${font DroidSans:size=12}${top_mem mem_res 2}${alignr}${top cpu 2}%${font}
${voffset 2}${font StyleBats:size=12}${color1}h${voffset -3}${font DroidSans:size=12}${color3}${offset 5}${top_mem name 3}${goto 150}${font DroidSans:size=12}${top_mem mem_res 3}${alignr}${top cpu 3}%${font}
##################################
##           NETWORK            ##
##################################
${voffset 6}${font DroidSans:bold:size=12}${color4}NETWORK${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 6}${font PizzaDudeBullets:size=11}${color2}T${font DroidSans:size=12}${color3}${offset 5}${voffset -2}Down${alignr}${font DroidSans:size=12}${downspeed wlan0}${font}
#${voffset 2}${font PizzaDudeBullets:size=11}${color2}N${font DroidSans:size=11}${color3}${offset 5}${voffset -2}Up${alignr}${font DroidSans:size=12}${upspeed wlan0}${font}
${voffset 4}${font PizzaDudeBullets:size=11}${color2}T${font DroidSans:size=11}${color3}${offset 5}${voffset -2}Downloaded${alignr}${font DroidSans:size=12}${totaldown wlan0}${font}
#${voffset 2}${font PizzaDudeBullets:size=11}${color2}N${font DroidSans:size=11}${color3}${offset 5}${voffset -2}Uploaded${alignr}${font DroidSans:size=12}${totalup wlan0}${font}
##################################
##      WEATHER (Imperial)      ##
##################################
#${voffset 6}${font DroidSans:bold:size=8}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
#${voffset 2}${goto 38}${font Weather:size=43.5}${color2}y${font}
#${voffset -50}${font RadioSpace:size=32}${color3}${alignc}${execi 1800 conkyForecast -d HT -i}${font}
#${voffset -33}${goto 199}${font DroidSansFallback:bold:size=7.55}${color6}H:${offset 1}${execpi 1800 conkyForecast -d HT -s 0 -ui | sed -e 's/N\/A'/'\$\{color7}TBA\$\{color6}/g'}${voffset 15}${goto 200}L:${offset 2}${execi 1800 conkyForecast -d LT -s 0 -ui}${font}
#${voffset -40}${font KRARound:size=36}${color7}${goto 185}I${font}
#${voffset 4}${font Ubuntu:size=23}${color4}${alignc}${execpi 1800 conkyForecast -d CT}${font}
#${voffset 12}${goto 20}${font ConkyWindNESW:size=41}${color3}${execi 1800 conkyForecast -d BS}${font}${voffset -40}${goto 98}${font ConkyWeather:size=45}${execi 1800 conkyForecast -d WF}${font}${voffset -39}${goto 188}${font MoonPhases:size=32}${execi 1800 conkyForecast -d MF}${font}
#${voffset 6}${goto 28}${font DroidSansFallback:bold:size=8.45}${color4}${execpi 1800 conkyForecast -d WS -i | sed -e 's/calm'/'\$\{offset 2}Calm/g' -e 's/mph'/'\$\{offset 3}mph/g'}${goto 88}Feels like ${execi 1800 conkyForecast -d LT -ui}${execpi 1800 conkyForecast -d MP| sed -e 's/First.*'/'\$\{goto 182}First Qtr/g' -e 's/Last.*'/'\$\{goto 184}Last Qtr/g' -e 's/New.*'/'\$\{goto 195}New/g' -e 's/Full.*'/'\$\{goto 195}Full/g' -e 's/Waning.*'/'\$\{goto 187}Waning/g' -e 's/Waxing.*'/'\$\{goto 187}Waxing/g'}${font}
#${voffset 9}${goto 36}${font DroidSansMono:bold:size=8.35}${color3}${execi 1800 conkyForecast -d DW -s 1 -w}${goto 89}${execi 1800 conkyForecast -d DW -s 2 -w}${goto 143}${execi 1800 conkyForecast -d DW -s 3 -w}${goto 197}${execi 1800 conkyForecast -d DW -s 4 -w}${font}
#${voffset 2}${goto 25}${font ConkyWeather:size=32}${color3}${execi 1800 conkyForecast -d WF -s 1 -e 4 -S 1}${font}
#${voffset 0}${goto 25}${font DroidSans:bold:size=8.5}${color4}${execi 1800 conkyForecast -d HT -s 1 -ui}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 1 -ui}${goto 79}${execi 1800 conkyForecast -d HT -s 2 -ui}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 2 -ui}${goto 133}${execi 1800 conkyForecast -d HT -s 3 -ui}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 3 -ui}${goto 187}${execi 1800 conkyForecast -d HT -s 4 -ui}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 4 -ui}${font}
##################################
##      WEATHER (Metric)        ##
##################################
#${voffset 6}${font DroidSans:bold:size=12}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}

#${voffset -2}${goto 20}${font Weather:size=43.5}${color2}y${font}
#${voffset -62}${font RadioSpace:size=40}${color3}${alignc}${execi 1800 conkyForecast --location=UKXX0092 -d HT}${font}
#${voffset -33}${goto 265}${font DroidSansFallback:bold:size=7.55}${color2}H:${offset 1}${execi 1800 conkyForecast --location=UKXX0092 -d HT -s 0}${voffset 15}${goto 265}L:${offset 2}${execi 1800 conkyForecast --location=UKXX0092 -d LT -s 0}${font}
#${voffset -45}${font KRARound:size=43}${color2}${goto 250}I${font}
#${voffset 6}${font Ubuntu:size=20}${color4}${alignc}${execi 1800 conkyForecast --location=UKXX0092 -d CT}${font}
#${voffset 12}${goto 5}${font ConkyWindNESW:size=41}${color3}${execi 1800 conkyForecast --location=UKXX0092 -d BS}${font}${voffset -38}${goto 130}${font ConkyWeather:size=45}${execi 1800 conkyForecast --location=UKXX0092 -d WF}${font}${voffset -40}${goto 260}${font MoonPhases:size=32}${execi 1800 conkyForecast --location=UKXX0092 -d MF}${font}
#${voffset 6}${goto 12}${font DroidSansFallback:bold:size=11}${color4}${execpi 1800 conkyForecast --location=UKXX0092 -d WS -i}${execpi 1800 conkyForecast --location=UKXX0092 -d MP | sed -e 's/First.*'/'\$\{alignr}First Qtr/g' -e 's/Last.*'/'\$\{alignr}Last Qtr/g' -e 's/New.*'/'\$\{alignr}New/g' -e 's/Full.*'/'\$\{alignr}Full/g' -e 's/Waning.*'/'\$\{alignr}Waning/g' -e 's/Waxing.*'/'\$\{alignr}Waxing/g'}${font}
#${voffset 9}${goto 15}${font DroidSansMono:bold:size=12}${color3}${execi 1800 conkyForecast --location=UKXX0092 -d DW -s 1 -w}${goto 92}${execi 1800 conkyForecast --location=UKXX0092 -d DW -s 2 -w}${goto 169}${execi 1800 conkyForecast --location=UKXX0092 -d DW -s 3 -w}${goto 246}${execi 1800 conkyForecast --location=UKXX0092 -d DW -s 4 -w}${font}
#${voffset 2}${goto 10}${font ConkyWeather:size=45}${color3}${execi 1800 conkyForecast --location=UKXX0092 -d WF -s 1 -e 4 -S 1}${font}
#${voffset 0}${goto 13}${font DroidSans:bold:size=11}${color4}${execi 1800 conkyForecast --location=UKXX0092 -d HT -s 1 -u}${offset 2}/${offset 2}${execi 1800 conkyForecast --location=UKXX0092 -d LT -s 1 -u}${goto 90}${execi 1800 conkyForecast --location=UKXX0092 -d HT -s 2 -u}${offset 2}/${offset 2}${execi 1800 conkyForecast --location=UKXX0092 -d LT -s 2 -u}${goto 165}${execi 1800 conkyForecast --location=UKXX0092 -d HT -s 3 -u}${offset 2}/${offset 2}${execi 1800 conkyForecast --location=UKXX0092 -d LT -s 3 -u}${goto 240}${execi 1800 conkyForecast --location=UKXX0092 -d HT -s 4 -u}${offset 2}/${offset 2}${execi 1800 conkyForecast --location=UKXX0092 -d LT -s 4 -u}${font}
##################################
##   BURY WEATHER (Metric)      ##
##################################
${font DroidSans:bold:size=12}${color4}BURY WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}${execi 600 bash /home/mdoo/accuweather_conky/accuw_script}

${font conkyweather:size=40}${color3}${execi 600  sed -n '2p' /home/mdoo/accuweather_conky/curr_cond}${font}${font DroidSans:size=11}${goto 75}${voffset -40}CURRENTLY: ${execpi 600 sed -n '4p' /home/mdoo/accuweather_conky/curr_cond}°C
${goto 75}${execpi 600 sed -n '3p' /home/mdoo/accuweather_conky/curr_cond|fold -s -w30}

${font conkyweather:size=40}${execi 600  sed -n '2p' /home/mdoo/accuweather_conky/tod_ton}${font}${font DroidSans:size=11}${goto 75}${voffset -40}${execpi 600 sed -n '1p' /home/mdoo/accuweather_conky/tod_ton}: ${execpi 600 sed -n '4p' /home/mdoo/accuweather_conky/tod_ton}°C / ${execpi 600 sed -n '5p' /home/mdoo/accuweather_conky/tod_ton}°C
${goto 75}${execpi 600 sed -n '3p' /home/mdoo/accuweather_conky/tod_ton|fold -s -w30}

${font conkyweather:size=40}${execi 600  sed -n '7p' /home/mdoo/accuweather_conky/tod_ton}${font}${font DroidSans:size=11}${goto 75}${voffset -40}${execpi 600 sed -n '6p' /home/mdoo/accuweather_conky/tod_ton}: ${execpi 600 sed -n '9p' /home/mdoo/accuweather_conky/tod_ton}°C / ${execpi 600 sed -n '10p' /home/mdoo/accuweather_conky/tod_ton}°C
${goto 75}${execpi 600 sed -n '8p' /home/mdoo/accuweather_conky/tod_ton|fold -s -w30}

${font conkyweather:size=40}${execi 600  sed -n '12p' /home/mdoo/accuweather_conky/tod_ton}${font}${font DroidSans:size=11}${goto 75}${voffset -40}${execpi 600 sed -n '11p' /home/mdoo/accuweather_conky/tod_ton}: ${execpi 600 sed -n '14p' /home/mdoo/accuweather_conky/tod_ton}°C / ${execpi 600 sed -n '15p' /home/mdoo/accuweather_conky/tod_ton}°C
${goto 75}${execpi 600 sed -n '13p' /home/mdoo/accuweather_conky/tod_ton|fold -s -w30}

${font conkyweather:size=40}${execi 600  sed -n '17p' /home/mdoo/accuweather_conky/tod_ton}${font}${font DroidSans:size=11}${goto 75}${voffset -40}${execpi 600 sed -n '16p' /home/mdoo/accuweather_conky/tod_ton}: ${execpi 600 sed -n '19p' /home/mdoo/accuweather_conky/tod_ton}°C / ${execpi 600 sed -n '20p' /home/mdoo/accuweather_conky/tod_ton}°C
${goto 75}${execpi 600 sed -n '18p' /home/mdoo/accuweather_conky/tod_ton|fold -s -w30}

${font conkyweather:size=40}${execi 600  sed -n '22p' /home/mdoo/accuweather_conky/tod_ton}${font}${font DroidSans:size=11}${goto 75}${voffset -40}${execpi 600 sed -n '21p' /home/mdoo/accuweather_conky/tod_ton}: ${execpi 600 sed -n '24p' /home/mdoo/accuweather_conky/tod_ton}°C / ${execpi 600 sed -n '25p' /home/mdoo/accuweather_conky/tod_ton}°C
${goto 75}${execpi 600 sed -n '23p' /home/mdoo/accuweather_conky/tod_ton|fold -s -w30}

##################################
##             TIME             ##
##################################
${voffset 6}${font DroidSans:bold:size=12}${color4}TIME${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset -4}${font RadioSpace:size=45}${color3}${if_match ${time %l}<=9}${alignc 7}${time %l:%M %p}${else}${if_match ${time %l}>=10}${alignc -1}${time %l:%M %p}${endif}${endif}${font}
#${voffset 3}${font DroidSansFallback:bold:size=12}${color4}${alignc 2}Sunrise${offset 1}${execi 1800 conkyForecast --location=UKXX0092 -d SR}${color3}${offset 2}|${offset 2}${color4}Sunset${offset 1}${execi 1800 conkyForecast --location=UKXX0092 -d SS}${font}

##################################
##           CALENDAR           ##
##################################
${voffset 4}${font DroidSans:bold:size=12}${color4}DATE${offset 8}${color8}${voffset -2}${hr 2}${font}
${offset 12}${voffset 20}${font DroidSansMono:size=10}${color3}${time %A}${font}
${offset 25}${voffset -4}${if_match ${time %e}<=9}${font DroidSansFallback:bold:size=28}${color5}${time %e}${font}${else}${if_match ${time %e}>=10}${font DroidSansFallback:bold:size=28}${color5}${time %e}${endif}${endif}${font}
${offset 30}${voffset 0}${font DroidSansMono:size=10}${color3}${time %B}${font}
${offset 30}${voffset 0}${font DroidSansMono:size=10}${color3}${time %Y}${font}
####
## Uncomment for Conky 1.8.0
#${voffset -85}${font DroidSansMono:size=10}${color3}${execpi 60 VinDSL_Cal_8=`date +%-d`; cal -h | sed -e '1d' -e s/^/"\$\{offset 130"\}/ -e 's/\<'"$VinDSL_Cal_8"'\>/${color4}&${color3}/'}
####
## Uncomment for Conky 1.8.1
${voffset -85}${offset 100}${font DroidSansMono:size=10}${color3}${execpi 60 VinDSL_Cal_9=`date +%-d`; cal -h | sed -e 's/\r//g' -e 's/^/ /g' -e '1d' -e 's/\<'"$VinDSL_Cal_9"'\>/${color4}&${color3}/'}${font}
#${voffset -130}${font CutOutsFor3DFX:size=85}${color8}2

```

---

### Post by sandyd on 2012-07-07
Use
```
exec sensors | grep "temp1" | cut -c6-
```

instead of
```
exec sensors | grep "temp1"
```

---

### Post by wildmanne39 on 2012-07-07
Hi, I am posting all my conky scripts with a screenshot.
.conkyrc
```
##################################
## VinDSL | rev. 11-04-23 22:16 ##
##################################
##      April Fools Series      ##
##################################

## ¡PLEASE READ THE FINE PRINT! ##

####
## Development Platforms (optional)
#
#  Ubuntu 10.10 'Maverick Meerkat'
#  Ubuntu 11.04 'Natty Narwhal'

####
## Prerequisites (required)
#
#  conky-all 1.8.0 or 1.8.1
#  conkyForecast 2.16 or newer 
#  Weather.com XML Data Feed (XOAP)
#  UTF-8 Compatible Text Editor

####
## Installed fonts (required)
#
#  ConkyWeather (Stanko Metodiev)
#  ConkyWindNESW (Stanko Metodiev)
#  Cut Outs for 3D FX (Fonts & Things)
#  Droid Font Family (Google Android SDK)
#  Moon Phases (Curtis Clark)
#  OpenLogos (Icoma)
#  PizzaDude Bullets (Jakob Fischer)
#  Radio Space (Iconian Fonts)
#  StyleBats (Vinterstille)
#  Ubuntu Font Family (Canonical Ltd)
#  Ubuntu Title Bold (Paulo Silva)
#  Weather (Jonathan Macagba)

####
## Use XFT? Required to Force UTF8 (see below)
#
use_xft yes
xftfont DroidSans:size=8.75
xftalpha 0.1

####
## Force UTF8? Requires XFT (see above)
## Displays degree symbol, instead of Â°, etc.
#
override_utf8_locale yes

####
## This buffer is used for text, single lines, output from $exec, and other variables.
## Increasing the text buffer size (too high) will drastically reduce Conky's performance.
## Decreasing the size (too low) will truncate content and cause strange display output.
## Standard text buffer size is 256 bytes (cannot be less). Adjust YOUR buffer wisely!
#
text_buffer_size 384

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
minimum_size 240 0

####
## Gap between text and screen borders.
#
gap_x 9
gap_x 5
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
cpu_avg_samples 4

####
## Number of net samples to average.
## Set to 1 to disable averaging.
#
net_avg_samples 4

####
## Add spaces to keep things from moving around?
## Only affects certain objects.
#
use_spacer right


####
## My colors (suit yourself)
#
color0 Red		#FFFFFF   
color1 Ivory		#FFFFF0
color2 Ivory2		#EEEEE0
color3 Ivory3		#CDCDC1
color4 Blue		#FFA54F
color5 Tan2		#EE9A49
color6 Gray		#7E7E7E
color7 AntiqueWhite4	#8B8378
color8 DimGray		#696969
color9 Green		#000000

#####
## Load Lua for shading (optional)
## Set the path to your script here.

lua_load /home/larry/.conky/draw_bg.lua
lua_draw_hook_pre draw_bg

####
## Load Lua for bargraphs (required)
## Set the path to your script here.
#

lua_load /home/larry/.conky/bargraph_small.lua
lua_draw_hook_post main_bars

TEXT
##################################
##             LOGO             ##
##################################
${voffset -33}${font OpenLogos:size=103}${color0}v${font}${voffset -76}${goto 178}${font UbuntuTitleBold:size=19.6}${color4}${offset 1}1${offset 5}2${offset 2}.04${font}
##################################
##            SYSTEM            ##
##################################
${voffset 20}${font DroidSans:bold:size=8.25}${color4}SYSTEM${offset 8}${color0}${voffset -2}${hr 2}${font}
${voffset 4}${font OpenLogos:size=10}${color2}u${voffset -4}${font DroidSans:size=8.65}${color3}${offset 5}${sysname}${offset 5}${kernel}${alignr}${font DroidSans:size=8.45}${machine}${font}
${voffset 2}${font StyleBats:size=10}${color2}A${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}Amd Phenom${offset 3}9150e${offset 3}Quad core${offset 3}${alignr}${font DroidSans:size=8.3}${freq_g cpu1}${offset 1}GHz${font}
${voffset 2}${font StyleBats:size=10}${color2}q${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}System${offset 3}Uptime${alignr}${font DroidSans:size=8.4}${uptime_short}${font}
${voffset 2}${font StyleBats:size=10}${color2}o${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}File${offset 3}System${alignr}${font DroidSans:size=8.5}${fs_type}${font}
##################################
##          PROCESSORS          ##
##################################
${voffset 6}${font DroidSans:bold:size=8}${color4}PROCESSORS${offset 8}${color0}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=9.9}${color2}k${voffset -2}${font DroidSansFallback:size=8.39}${color3}${offset 2}CPU1${offset 5}${font DroidSans:size=8.3}${cpu cpu1}%${font}
${voffset 2}${font StyleBats:size=9.9}${color2}k${voffset -2}${font DroidSansFallback:size=8.39}${color3}${offset 2}CPU2${offset 5}${font DroidSans:size=8.3}${cpu cpu2}%${font}
${voffset 2}${font StyleBats:size=9.9}${color2}k${voffset -2}${font DroidSansFallback:size=8.39}${color3}${offset 2}CPU3${offset 5}${font DroidSans:size=8.3}${cpu cpu3}%${font}
${voffset 2}${font StyleBats:size=9.9}${color2}k${voffset -2}${font DroidSansFallback:size=8.39}${color3}${offset 2}CPU4${offset 5}${font DroidSans:size=8.3}${cpu cpu4}%${font}
##################################
##            MEMORY            ##
##################################

${voffset 6}${font DroidSans:bold:size=8}${color4}MEMORY${offset 8}${color0}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=10}${color2}l${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 3}RAM${goto 97}${font DroidSans:size=8.3}${mem}${goto 133}/${offset 5}${memmax}${alignr}${memperc}%${font}
##################################
##             HDD              ##
##################################
${voffset 16}${font DroidSans:bold:size=8}${color4}HDD${offset 8}${color0}${voffset -2}${hr 2}${font}
${voffset 5}${font StyleBats:size=9.9}${color2}x${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}ROOT${goto 95}${font DroidSans:size=8.3}${fs_used /}${goto 133}/${offset 5}${fs_size /}${alignr}${fs_free_perc /}%${font}
${voffset 15}${font StyleBats:size=9.9}${color2}x${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}HOME${goto 95}${font DroidSans:size=8.3}${fs_used /home}${goto 133}/${offset 5}${fs_size /home}${alignr}${fs_free_perc /home}%${font}
${voffset 15}${font StyleBats:size=9.9}${color2}4${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}SWAP${goto 95}${font DroidSans:size=8.3}${swap}${goto 133}/${offset 5}${swapmax}${alignr}${swapperc}%${font}
##################################
##         TOP PROCESSES        ##
##################################
${voffset 16}${font DroidSans:bold:size=8}${color4}TOP PROCESSES${offset 8}${color0}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 1}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 1}${alignr}${top_mem mem 1}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 2}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 2}${alignr}${top_mem mem 2}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 3}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 3}${alignr}${top_mem mem 3}%${font}
${voffset 2}${if_running rhythmbox}${voffset -16}${else}${if_running banshee}${voffset -16}${else}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 4}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 4}${alignr}${top_mem mem 4}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 5}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 5}${alignr}${top_mem mem 5}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 6}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 6}${alignr}${top_mem mem 6}%${endif}${endif}${font}
##################################
##           NETWORK            ##
##################################
${voffset 6}${font DroidSans:bold:size=8}${color4}NETWORK${offset 8}${color0}${voffset -2}${hr 2}${font}
${voffset 4}${font PizzaDudeBullets:size=9.5}${color6}a${font DroidSans:size=8.5}${color3}${offset 5}Private${offset 3}IP${alignr}${font DroidSans:size=8.3}${addr eth0}${font}
${voffset 0}${font PizzaDudeBullets:size=9.5}${color6}a${font DroidSans:size=8.5}${color3}${offset 5}Public${offset 7}IP${alignr}${font DroidSans:size=8.3}${execi 1800 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}${font}
${voffset 4}${font PizzaDudeBullets:size=9.5}${color6}T${font DroidSans:size=8.5}${color3}${offset 5}Down${alignr}${font DroidSans:size=8.3}${downspeed eth0}${font}
${voffset 0}${font PizzaDudeBullets:size=9.5}${color6}N${font DroidSans:size=8.5}${color3}${offset 5}Up${alignr}${font DroidSans:size=8.3}${upspeed eth0}${font}
${voffset 4}${font PizzaDudeBullets:size=9.5}${color6}T${font DroidSans:size=8.5}${color3}${offset 5}Downloaded${alignr}${font DroidSans:size=8.3}${totaldown eth0}${font}
${voffset 0}${font PizzaDudeBullets:size=9.5}${color6}N${font DroidSans:size=8.5}${color3}${offset 5}Uploaded${alignr}${font DroidSans:size=8.3}${totalup eth0}${font}
##################################
##     WEATHER (Imperial)       ##
##################################
${voffset 4}${font DroidSans:bold:size=8.25}${color4}WEATHER${offset 8}${color0}${voffset -2}${hr 2}${font}
${voffset -55}${font RadioSpace:size=34}${color3}${execi 1800 /home/larry/.conky/weather/weather.sh "Roswell,NM" ctbi}${font}${voffset -28}${goto 33}${font Weather:size=42}${color3}y${font}
${voffset -38}${font Ubuntu:size=8.63}${color3}${execi 1800 /home/larry/.conky/weather/weather.sh "Roswell,NM" ctti}${font}
${voffset -39}${font KRARound:size=36}${color3}${goto 195}I${font}
${voffset 6}${font Ubuntu:size=23}${color4}${alignc -2}${execi 1800 /home/larry/.conky/weather/weather.sh "Roswell,NM" ccb}${font}
${voffset 8}${font DroidSansFallback:size=8.63}${color3}${execi 1800 /home/larry/.conky/weather/weather.sh "Roswell,NM"}${font}
${voffset -57}${font ConkyWeather:size=48}${color6}${alignc -55}${execi 1800 /home/larry/.conky/weather/weather.sh "Roswell,NM" cp}${font}
${voffset 6}${font DroidSansMono:bold:size=8.62}${color4}${offset 40}${execi 1800 /home/larry/.conky/weather/weather.sh "Roswell,NM" dl}${font}
${voffset 0}${font ConkyWeather:size=37.9}${color3}${offset 26}${execi 1800 /home/larry/.conky/weather/weather.sh "Roswell,NM" fcp}${font}
${voffset 0}${font DroidSansFallback:bold:size=8.62}${color4}${offset 28}${execi 1800 /home/larry/.conky/weather/weather.sh "Roswell,NM" fcti}${font}
##################################
##      WEATHER (Metric)        ##
##################################
# ${voffset 4}${font DroidSans:bold:size=8.25}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
# ${voffset -55}${font RadioSpace:size=34}${color3}${execi 1800 /home/vindsl/.conky/weather/weather.sh "Toronto" ctbm}${font}${voffset -28}${goto 33}${font Weather:size=42}${color3}y${font}
# ${voffset -38}${font Ubuntu:size=8.63}${color5}${execi 1800 /home/vindsl/.conky/weather/weather.sh "Toronto" cttm}${font}
# ${voffset -39}${font KRARound:size=36}${color3}${goto 195}I${font}
# ${voffset 6}${font Ubuntu:size=23}${color5}${alignc -2}${execi 1800 /home/vindsl/.conky/weather/weather.sh "Toronto" ccb}${font}
# ${voffset 8}${font DroidSansFallback:size=8.63}${color3}${execi 1800 /home/vindsl/.conky/weather/weather.sh "Toronto"}${font}
# ${voffset -57}${font ConkyWeather:size=48}${color6}${alignc -55}${execi 1800 /home/vindsl/.conky/weather/weather.sh "Toronto" cp}${font}
# ${voffset 6}${font DroidSansMono:bold:size=8.62}${color4}${offset 40}${execi 1800 /home/vindsl/.conky/weather/weather.sh "Toronto" dl}${font}
# ${voffset 0}${font ConkyWeather:size=37.9}${color3}${offset 26}${execi 1800 /home/vindsl/.conky/weather/weather.sh "Toronto" fcp}${font}
# ${voffset 0}${font DroidSansFallback:bold:size=8.62}${color4}${offset 35}${execi 1800 /home/vindsl/.conky/weather/weather.sh "Toronto" fctm}${font}

##################################
##             TIME             ##
##################################
${voffset 6}${font DroidSans:bold:size=8}${color4}TIME${offset 8}${color0}${voffset -2}${hr 2}${font}
${voffset -4}${font RadioSpace:size=32}${color3}${if_match ${time %l}<=9}${alignc 7}${time %l:%M%p}${else}${if_match ${time %l}>=10}${alignc -1}${time %l:%M%p}${endif}${endif}${font}
${voffset 0}${font DroidSansFallback:bold:size=6.85}${color4}${alignc 2} Sunrise${offset 1}${execi 1800 conkyForecast -d SR}${color3}${offset 2}|${offset 2}${color4}Sunset${offset 1}${execi 1800 conkyForecast -d SS}${font}
##################################
##           CALENDAR           ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}DATE${offset 8}${color0}${voffset -2}${hr 2}${font}
${voffset 16}${font DroidSansMono:size=7.55}${color3}${alignc 60}${time %A}${font}
${voffset -4}${font DroidSansFallback:bold:size=18}${if_match ${time %e}<=9}${color4}${alignc 65}${time %e}${font}${else}${if_match ${time %e}>=10}${color3}${alignc 60}${time %e}${endif}${endif}${font}
${voffset 0}${font DroidSansMono:size=7.55}${color3}${alignc 60}${time %B}${font}
${voffset 0}${font DroidSansMono:size=7.6}${color3}${alignc 60}${time %Y}${font}
####
## Uncomment for Conky 1.8.0
#${voffset -75}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_8=`date +%-d`; cal -h | sed -e 's/\r//g' -e '1d' -e s/^/"\$\{offset 105"\}/ -e 's/\<'"$VinDSL_Cal_8"'\>/${color4}&${color3}/'}${font}
####
##Uncomment for Conky 1.8.1
##Uncomment for Conky 1.8.1
${voffset -75}${offset 115}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_8=`date +%-d`; cal -h | sed -e '1d' -e 's/\<'"$VinDSL_Cal_8"'\>/${color4}&${color3}/'}
${voffset -98}${offset 30}${font CutOutsFor3DFX:size=67}${color8}${alignc 99}2${font}
##################################
##          RHYTHMBOX           ##
##################################
#${if_running rhythmbox}${voffset 21}${font DroidSans:bold:size=7.75}${color4}RHYTHMBOX${offset 8}${color0}${voffset -2}${hr 2}${endif}${font}
${if_running rhythmbox}${voffset 10}${font DroidSans:size=12}${color2}${if_match "${execpi 2 expr length "`/usr/bin/rhythmbox-client --print-playing-format %tt | head -n 1`"}" >= "45"}${alignr}${scroll 38 4* ${execi 2 rhythmbox-client --print-playing-format %tt --no-start}}${font}${else}${alignc}${execi 2 rhythmbox-client --print-playing-format %tt --no-start}${endif}${endif}${font}
##################################
##    BANSHEE (Experimental)    ##
##################################
${if_running banshee}${voffset 15}${font DroidSans:bold:size=7.75}${color4}BANSHEE${offset 8}${color0}${voffset -2}${hr 2}${voffset 31}${endif}${font}
${if_running banshee}${voffset -24}${font DroidSans:size=8.25}${color3}${if_match "${execpi 10 expr length "`/usr/bin/banshee --query-title --no-present | cut -f1- -d " "`"}" >= "50"}${alignr}${scroll 45 4* ${execi 10 banshee --query-title --no-present | cut -f2- -d " "}}${font}${else}${alignc}${execi 10 banshee --query-title --no-present | cut -f2- -d " "}${endif}${endif}${font}


```
small.lau
```
--[[ BARGRAPH WIDGET
	v2.1 by wlourf (07 Jan. 2011)
	this widget draws a bargraph with different effects 
	http://u-scripts.blogspot.com/2010/07/bargraph-widget.html
	
To call the script in a conky, use, before TEXT
	lua_load /path/to/the/script/bargraph.lua
	lua_draw_hook_pre main_rings
and add one line (blank or not) after TEXT
	
Parameters are :
3 parameters are mandatory
name	- the name of the conky variable to display, for example for {$cpu cpu0}, just write name="cpu"
arg		- the argument of the above variable, for example for {$cpu cpu0}, just write arg="cpu0"
		  arg can be a numerical value if name=""
max		- the maximum value the above variable can reach, for example, for {$cpu cpu0}, just write max=100
	
Optional parameters:
x,y		- coordinates of the starting point of the bar, default = middle of the conky window
cap		- end of cap line, ossibles values are r,b,s (for round, butt, square), default="b"
		  http://www.cairographics.org/samples/set_line_cap/
angle	- angle of rotation of the bar in degress, default = 0 (i.e. a vertical bar)
		  set to 90 for an horizontal bar
skew_x	- skew bar around x axis, default = 0
skew_y	- skew bar around y axis, default = 0
blocks  - number of blocks to display for a bar (values >0) , default= 10
height	- height of a block, default=10 pixels
width	- width of a block, default=20 pixels
space	- space between 2 blocks, default=2 pixels
angle_bar	- this angle is used to draw a bar on a circular way (ok, this is no more a bar !) default=0
radius		- for cicular bars, internal radius, default=0
			  with radius, parameter width has no more effect.

Colours below are defined into braces {colour in hexadecimal, alpha}
fg_colour	- colour of a block ON, default= {0x00FF00,1}
bg_colour	- colour of a block OFF, default = {0x00FF00,0.5}
alarm		- threshold, values after this threshold will use alarm_colour colour , default=max
alarm_colour - colour of a block greater than alarm, default=fg_colour
smooth		- (true or false), create a gradient from fg_colour to bg_colour, default=false 
mid_colour	- colours to add to gradient, with this syntax {position into the gradient (0 to1), colour hexa, alpha}
			  for example, this table {{0.25,0xff0000,1},{0.5,0x00ff00,1},{0.75,0x0000ff,1}} will add
			  3 colurs to gradient created by fg_colour and alarm_colour, default=no mid_colour
led_effect	- add LED effects to each block, default=no led_effect
			  if smooth=true, led_effect is not used
			  possibles values : "r","a","e" for radial, parallelel, perdendicular to the bar (just try!)
			  led_effect has to be used with theses colours :
fg_led		- middle colour of a block ON, default = fg_colour
bg_led		- middle colour of a block OFF, default = bg_colour
alarm_led	- middle colour of a block > ALARM,  default = alarm_colour

reflection parameters, not avaimable for circular bars
reflection_alpha    - add a reflection effect (values from 0 to 1) default = 0 = no reflection
                      other values = starting opacity
reflection_scale    - scale of the reflection (default = 1 = height of text)
reflection_length   - length of reflection, define where the opacity will be set to zero
					  calues from 0 to 1, default =1
reflection			- position of reflection, relative to a vertical bar, default="b"
					  possibles values are : "b","t","l","r" for bottom, top, left, right
draw_me     - if set to false, text is not drawn (default = true or 1)
              it can be used with a conky string, if the string returns 1, the text is drawn :
              example : "${if_empty ${wireless_essid wlan0}}${else}1$endif",

v1.0 (10 Feb. 2010) original release
v1.1 (13 Feb. 2010) numeric values can be passed instead conky stats with parameters name="", arg = numeric_value	
v1.2 (28 Feb. 2010) just renamed the widget to bargraph
v1.3 (03 Mar. 2010) added parameters radius & angle_bar to draw the bar in a circular way
v2.0 (12 Jul. 2010) rewrite script + add reflection effects and parameters are now set into tables
v2.1 (07 Jan. 2011) Add draw_me parameter and correct memory leaks, thanks to "Creamy Goodness"

--      This program is free software; you can redistribute it and/or modify
--      it under the terms of the GNU General Public License as published by
--      the Free Software Foundation version 3 (GPLv3)
--     
--      This program is distributed in the hope that it will be useful,
--      but WITHOUT ANY WARRANTY; without even the implied warranty of
--      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
--      GNU General Public License for more details.
--     
--      You should have received a copy of the GNU General Public License
--      along with this program; if not, write to the Free Software
--      Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
--      MA 02110-1301, USA.		

]]

require 'cairo'

----------------START OF PARAMETERS ----------
function conky_main_bars()
	local bars_settings={
		{	--[ Graph for CPU1 ]--
			name="cpu",
			arg="cpu1",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=80,y=161,
			blocks=55,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},
		{	--[ Graph for CPU2 ]--
			name="cpu",
			arg="cpu2",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=80,y=175,
			blocks=55,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},
                {	--[ Graph for CPU3 ]--
			name="cpu",
			arg="cpu3",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=80,y=190,
			blocks=55,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
                        },
                {	--[ Graph for CPU4 ]--
			name="cpu",
			arg="cpu4",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=80,y=204,
			blocks=55,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
                        },
		{	--[ Graph for Memory ]--
			name="memperc",
			arg="",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=15,y=266,
			blocks=77,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},
		{	--[ Graph for Root ]--
                        name="fs_used_perc",
			arg="/",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=15,y=312,
			blocks=77,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},	
		{	--[ Graph for Home ]--
			name="fs_used_perc",
			arg="/home",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=15,y=340,
			blocks=77,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},	
	        {	--[ Graph for Swap ]--
                        name="swapperc",
			arg="",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=15,y=368,
			blocks=77,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},
		 }	
-----------END OF PARAMETERS--------------


    
	if conky_window == nil then return end
	
	local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
	
	cr = cairo_create(cs)    
	--prevent segmentation error when reading cpu state
    if tonumber(conky_parse('${updates}'))>3 then
        for i in pairs(bars_settings) do
        	
        	draw_multi_bar_graph(bars_settings[i])
        	
        end
    end
	cairo_destroy(cr)
	cairo_surface_destroy(cs)
	cr=nil

end



function draw_multi_bar_graph(t)
	cairo_save(cr)
	--check values
	if t.draw_me == true then t.draw_me = nil end
	if t.draw_me ~= nil and conky_parse(tostring(t.draw_me)) ~= "1" then return end	
	if t.name==nil and t.arg==nil then 
		print ("No input values ... use parameters 'name' with 'arg' or only parameter 'arg' ") 
		return
	end
	if t.max==nil then
		print ("No maximum value defined, use 'max'")
		return
	end
	if t.name==nil then t.name="" end
	if t.arg==nil then t.arg="" end

	--set default values	
	if t.x == nil		then t.x = conky_window.width/2 end
	if t.y == nil		then t.y = conky_window.height/2 end
	if t.blocks == nil	then t.blocks=10 end
	if t.height == nil	then t.height=10 end
	if t.angle == nil 	then t.angle=0 end
	t.angle = t.angle*math.pi/180
	--line cap style
	if t.cap==nil		then t.cap = "b" end
	local cap="b"
	for i,v in ipairs({"s","r","b"}) do 
		if v==t.cap then cap=v end
	end
	local delta=0
	if t.cap=="r" or t.cap=="s" then delta = t.height end
	if cap=="s" then 	cap = CAIRO_LINE_CAP_SQUARE
	elseif cap=="r" then
		cap = CAIRO_LINE_CAP_ROUND
	elseif cap=="b" then
		cap = CAIRO_LINE_CAP_BUTT
	end
	--end line cap style
	--if t.led_effect == nil	then t.led_effect="r" end
	if t.width == nil	then t.width=20 end
	if t.space == nil	then t.space=2 end
	if t.radius == nil	then t.radius=0 end
	if t.angle_bar == nil	then t.angle_bar=0 end
	t.angle_bar = t.angle_bar*math.pi/360 --halt angle
	
	--colours
	if t.bg_colour == nil 	then t.bg_colour = {0x00FF00,0.5} end
	if #t.bg_colour~=2 		then t.bg_colour = {0x00FF00,0.5} end
	if t.fg_colour == nil 	then t.fg_colour = {0x00FF00,1} end
	if #t.fg_colour~=2 		then t.fg_colour = {0x00FF00,1} end
	if t.alarm_colour == nil 	then t.alarm_colour = t.fg_colour end
	if #t.alarm_colour~=2 		then t.alarm_colour = t.fg_colour end

	if t.mid_colour ~= nil then	
		for i=1, #t.mid_colour do    
		    if #t.mid_colour[i]~=3 then 
		    	print ("error in mid_color table")
		    	t.mid_colour[i]={1,0xFFFFFF,1} 
		    end
		end
    end
    
	if t.bg_led ~= nil and #t.bg_led~=2	then t.bg_led = t.bg_colour end
	if t.fg_led ~= nil and #t.fg_led~=2	then t.fg_led = t.fg_colour end
	if t.alarm_led~= nil and #t.alarm_led~=2 then t.alarm_led = t.fg_led end
	
	if t.led_effect~=nil then
		if t.bg_led == nil then t.bg_led = t.bg_colour end
		if t.fg_led == nil 	then t.fg_led = t.fg_colour end
		if t.alarm_led == nil  then t.alarm_led = t.fg_led end
	end
	

	if t.alarm==nil then t.alarm = t.max end --0.8*t.max end
	if t.smooth == nil then t.smooth = false end

	if t.skew_x == nil then 
		t.skew_x=0 
	else
		t.skew_x = math.pi*t.skew_x/180	
	end
	if t.skew_y == nil then 
		t.skew_y=0
	else
		t.skew_y = math.pi*t.skew_y/180	
	end
	
	if t.reflection_alpha==nil then t.reflection_alpha=0 end
	if t.reflection_length==nil then t.reflection_length=1 end
	if t.reflection_scale==nil then t.reflection_scale=1 end
	
	--end of default values
	

 	local function rgb_to_r_g_b(col_a)
		return ((col_a[1] / 0x10000) % 0x100) / 255., ((col_a[1] / 0x100) % 0x100) / 255., (col_a[1] % 0x100) / 255., col_a[2]
	end
	
	
	--functions used to create patterns

	local function create_smooth_linear_gradient(x0,y0,x1,y1)
		local pat = cairo_pattern_create_linear (x0,y0,x1,y1)
		cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(t.fg_colour))
		cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(t.alarm_colour))
		if t.mid_colour ~=nil then
			for i=1, #t.mid_colour do
				cairo_pattern_add_color_stop_rgba (pat, t.mid_colour[i][1], rgb_to_r_g_b({t.mid_colour[i][2],t.mid_colour[i][3]}))
			end
		end
		return pat
	end

	local function create_smooth_radial_gradient(x0,y0,r0,x1,y1,r1)
		local pat =  cairo_pattern_create_radial (x0,y0,r0,x1,y1,r1)
		cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(t.fg_colour))
		cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(t.alarm_colour))
		if t.mid_colour ~=nil then
			for i=1, #t.mid_colour do
				cairo_pattern_add_color_stop_rgba (pat, t.mid_colour[i][1], rgb_to_r_g_b({t.mid_colour[i][2],t.mid_colour[i][3]}))
			end
		end
		return pat
	end
	
	local function create_led_linear_gradient(x0,y0,x1,y1,col_alp,col_led)
		local pat = cairo_pattern_create_linear (x0,y0,x1,y1) ---delta, 0,delta+ t.width,0)
		cairo_pattern_add_color_stop_rgba (pat, 0.0, rgb_to_r_g_b(col_alp))
		cairo_pattern_add_color_stop_rgba (pat, 0.5, rgb_to_r_g_b(col_led))
		cairo_pattern_add_color_stop_rgba (pat, 1.0, rgb_to_r_g_b(col_alp))
		return pat
	end

	local function create_led_radial_gradient(x0,y0,r0,x1,y1,r1,col_alp,col_led,mode)
		local pat = cairo_pattern_create_radial (x0,y0,r0,x1,y1,r1)
		if mode==3 then
			cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(col_alp))				
			cairo_pattern_add_color_stop_rgba (pat, 0.5, rgb_to_r_g_b(col_led))
			cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(col_alp))				
		else
			cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(col_led))
			cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(col_alp))				
		end
		return pat
	end






	local function draw_single_bar()
		--this fucntion is used for bars with a single block (blocks=1) but 
		--the drawing is cut in 3 blocks : value/alarm/background
		--not zvzimzblr for circular bar
		local function create_pattern(col_alp,col_led,bg)
			local pat
			
			if not t.smooth then
				if t.led_effect=="e" then
					pat = create_led_linear_gradient (-delta, 0,delta+ t.width,0,col_alp,col_led)
				elseif t.led_effect=="a" then
					pat = create_led_linear_gradient (t.width/2, 0,t.width/2,-t.height,col_alp,col_led)
				elseif  t.led_effect=="r" then
					pat = create_led_radial_gradient (t.width/2, -t.height/2, 0, t.width/2,-t.height/2,t.height/1.5,col_alp,col_led,2)
				else
					pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(col_alp))
				end
			else
				if bg then
					pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(t.bg_colour))
				else
					pat = create_smooth_linear_gradient(t.width/2, 0, t.width/2,-t.height)
				end
			end
			return pat
		end
		
		local y1=-t.height*pct/100
		local y2,y3
		if pct>(100*t.alarm/t.max) then 
			y1 = -t.height*t.alarm/100
			y2 = -t.height*pct/100
			if t.smooth then y1=y2 end
		end
		
		if t.angle_bar==0 then
		
			--block for fg value
			local pat = create_pattern(t.fg_colour,t.fg_led,false)
			cairo_set_source(cr,pat)
			cairo_rectangle(cr,0,0,t.width,y1)
			cairo_fill(cr)
			cairo_pattern_destroy(pat)
		
			-- block for alarm value			
			if not t.smooth and y2 ~=nil then 
				pat = create_pattern(t.alarm_colour,t.alarm_led,false)
				cairo_set_source(cr,pat)
				cairo_rectangle(cr,0,y1,t.width,y2-y1)
				cairo_fill(cr)
				y3=y2
				cairo_pattern_destroy(pat)
			else
				y2,y3=y1,y1
			end
			-- block for bg value
			cairo_rectangle(cr,0,y2,t.width,-t.height-y3)
			pat = create_pattern(t.bg_colour,t.bg_led,true)
			cairo_set_source(cr,pat)
			cairo_pattern_destroy(pat)
			cairo_fill(cr)
		end		
	end  --end single bar
	





	local function draw_multi_bar()
		--function used for bars with 2 or more blocks
		for pt = 1,t.blocks do 
			--set block y
			local y1 = -(pt-1)*(t.height+t.space)
			local light_on=false
			
			--set colors
			local col_alp = t.bg_colour
			local col_led = t.bg_led
			if pct>=(100/t.blocks) or pct>0 then --ligth on or not the block
				if pct>=(pcb*(pt-1))  then 
					light_on = true
					col_alp = t.fg_colour
					col_led = t.fg_led
					if pct>=(100*t.alarm/t.max) and (pcb*pt)>(100*t.alarm/t.max) then 
						col_alp = t.alarm_colour 
						col_led = t.alarm_led 
					end
				end
			end

			--set colors
			--have to try to create gradients outside the loop ?
			local pat 
			
			if not t.smooth then
				if t.angle_bar==0 then
					if t.led_effect=="e" then
						pat = create_led_linear_gradient (-delta, 0,delta+ t.width,0,col_alp,col_led)
					elseif t.led_effect=="a" then
						pat = create_led_linear_gradient (t.width/2, -t.height/2+y1,t.width/2,0+t.height/2+y1,col_alp,col_led)					
					elseif  t.led_effect=="r" then
						pat = create_led_radial_gradient (t.width/2, y1, 0, t.width/2,y1,t.width/1.5,col_alp,col_led,2)	
					else
						pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(col_alp))
					end
				else
					 if t.led_effect=="a"  then
						 pat = create_led_radial_gradient (0, 0, t.radius+(t.height+t.space)*(pt-1),
														 0, 0, t.radius+(t.height+t.space)*(pt),						 
											 col_alp,col_led,3)	
					else
						pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(col_alp))					
					end
					
				end
			else
				
				if light_on then
					if t.angle_bar==0 then
						pat = create_smooth_linear_gradient(t.width/2, t.height/2, t.width/2,-(t.blocks-0.5)*(t.height+t.space))
					else
						pat = create_smooth_radial_gradient(0, 0, (t.height+t.space),  0,0,(t.blocks+1)*(t.height+t.space),2)
					end
				else		
					pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(t.bg_colour))
				end
			end
			cairo_set_source (cr, pat)
			cairo_pattern_destroy(pat)

			--draw a block
			if t.angle_bar==0 then
				cairo_move_to(cr,0,y1)
				cairo_line_to(cr,t.width,y1)
			else		
				cairo_arc( cr,0,0,
					t.radius+(t.height+t.space)*(pt)-t.height/2,
					 -t.angle_bar -math.pi/2 ,
					 t.angle_bar -math.pi/2)
			end
			cairo_stroke(cr)
		end	
	end
	
	
	
	
	local function setup_bar_graph()
		--function used to retrieve the value to display and to set the cairo structure
		if t.blocks ~=1 then t.y=t.y-t.height/2 end
		
		local value = 0
		if t.name ~="" then
			value = tonumber(conky_parse(string.format('${%s %s}', t.name, t.arg)))
			--$to_bytes doesn't work when value has a decimal point,
			--https://garage.maemo.org/plugins/ggit/browse.php/?p=monky;a=commitdiff;h=174c256c81a027a2ea406f5f37dc036fac0a524b;hp=d75e2db5ed3fc788fb8514121f67316ac3e5f29f
			--http://sourceforge.net/tracker/index.php?func=detail&aid=3000865&group_id=143975&atid=757310
			--conky bug?
			--value = (conky_parse(string.format('${%s %s}', t.name, t.arg)))
			--if string.match(value,"%w") then
			--	value = conky_parse(string.format('${to_bytes %s}',value))
			--end
		else
			value = tonumber(t.arg)
		end

		if value==nil then value =0 end
		
		pct = 100*value/t.max
		pcb = 100/t.blocks
		
		cairo_set_line_width (cr, t.height)
		cairo_set_line_cap  (cr, cap)
		cairo_translate(cr,t.x,t.y)
		cairo_rotate(cr,t.angle)

		local matrix0 = cairo_matrix_t:create()
		tolua.takeownership(matrix0)
		cairo_matrix_init (matrix0, 1,t.skew_y,t.skew_x,1,0,0)
		cairo_transform(cr,matrix0)

	
		
		--call the drawing function for blocks
		if t.blocks==1 and t.angle_bar==0 then
			draw_single_bar()
			if t.reflection=="t" or t.reflection=="b" then cairo_translate(cr,0,-t.height) end
		else
			draw_multi_bar()
		end

		--dot for reminder
		--[[
		if t.blocks ~=1 then
			cairo_set_source_rgba(cr,1,0,0,1)
			cairo_arc(cr,0,t.height/2,3,0,2*math.pi)
			cairo_fill(cr)
		else
			cairo_set_source_rgba(cr,1,0,0,1)
			cairo_arc(cr,0,0,3,0,2*math.pi)
			cairo_fill(cr)
		end]]
		
		--call the drawing function for reflection and prepare the mask used		
		if t.reflection_alpha>0 and t.angle_bar==0 then
			local pat2
			local matrix1 = cairo_matrix_t:create()
			tolua.takeownership(matrix1)
			if t.angle_bar==0 then
				pts={-delta/2,(t.height+t.space)/2,t.width+delta,-(t.height+t.space)*(t.blocks)}
				if t.reflection=="t" then
					cairo_matrix_init (matrix1,1,0,0,-t.reflection_scale,0,-(t.height+t.space)*(t.blocks-0.5)*2*(t.reflection_scale+1)/2)
					pat2 = cairo_pattern_create_linear (t.width/2,-(t.height+t.space)*(t.blocks),t.width/2,(t.height+t.space)/2)
				elseif t.reflection=="r" then
					cairo_matrix_init (matrix1,-t.reflection_scale,0,0,1,delta+2*t.width,0)
					pat2 = cairo_pattern_create_linear (delta/2+t.width,0,-delta/2,0)
				elseif t.reflection=="l" then
					cairo_matrix_init (matrix1,-t.reflection_scale,0,0,1,-delta,0)
					pat2 = cairo_pattern_create_linear (-delta/2,0,delta/2+t.width,-0)
				else --bottom
					cairo_matrix_init (matrix1,1,0,0,-1*t.reflection_scale,0,(t.height+t.space)*(t.reflection_scale+1)/2)
					pat2 = cairo_pattern_create_linear (t.width/2,(t.height+t.space)/2,t.width/2,-(t.height+t.space)*(t.blocks))
				end
			end
			cairo_transform(cr,matrix1)

			if t.blocks==1 and t.angle_bar==0 then
				draw_single_bar()
				cairo_translate(cr,0,-t.height/2) 
			else
				draw_multi_bar()
			end
			
			
			cairo_set_line_width(cr,0.01)
			cairo_pattern_add_color_stop_rgba (pat2, 0,0,0,0,1-t.reflection_alpha)
			cairo_pattern_add_color_stop_rgba (pat2, t.reflection_length,0,0,0,1)
			if t.angle_bar==0 then
				cairo_rectangle(cr,pts[1],pts[2],pts[3],pts[4])
			end
			cairo_clip_preserve(cr)
			cairo_set_operator(cr,CAIRO_OPERATOR_CLEAR)
			cairo_stroke(cr)
			cairo_mask(cr,pat2)
			cairo_pattern_destroy(pat2)
			cairo_set_operator(cr,CAIRO_OPERATOR_OVER)
			
		end --reflection
		pct,pcb=nil
	end --setup_bar_graph()
	
	--start here !
	setup_bar_graph()
	cairo_restore(cr)
end


```
draw_bg.lua
```
--[[	Background by londonali1010 (2009)
	VinDSL Background Hack (2010-2011)

This script draws a background to the Conky window. It covers the whole of the Conky window, but you can specify rounded corners, if you wish.

To call this script in Conky, use (assuming you have saved this script to ~/scripts/):
	lua_load ~/scripts/draw_bg.lua
	lua_draw_hook_pre draw_bg

Changelog:
	+ v3.0	VinDSL Hack (01.28.2011) Killed memory leak.
	+ v2.4	VinDSL Hack (01.25.2011) Declared all variables in local.
	+ v2.3	VinDSL Hack (12.31.2010) Added shading example(s).
	+ v2.2	VinDSL Hack (12.30.2010) Cleaned up the code a bit.
	+ v2.1	VinDSL Hack (12.24.2010) Added cairo destroy function(s).
	+ v2.0	VinDSL Hack (12.21.2010) Added height adjustment variable.
	+ v1.0	Original release (07.10.2009)

]]

--------------START OF PARAMETERS ------------
-- Change these settings to affect your background:

-- "corner_r" is the radius, in pixels, of the rounded corners. If you don't want rounded corners, use 0.

	local corner_r = 50

-- Set the colour and transparency (alpha) of your background (0.00 - 0.99).

--	(Light Shading Example)
--	local bg_colour = 0x4d4d4d
--	local bg_alpha = 0.50

--	(Medium Shading Example)
--	local bg_colour = 0x222222
--	local bg_alpha = 0.50

--	(Dark Shading Example)
--	local bg_colour = 0x000000
--	local bg_alpha = 0.50

	local bg_colour = 0x222222
	local bg_alpha = 0.20

-- Tweaks the height of your background, in pixels. If you don't need to adjust the height, use 0.

--	(Default Setting)
--	local vindsl_hack_height = 100
	local vindsl_hack_height = -228
---------------END OF PARAMETERS -------------

require 'cairo'
local	cs, cr = nil

local function rgb_to_r_g_b(colour,alpha)
	return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
	end

function conky_draw_bg()
	if conky_window == nil then return end
	if cs == nil then cairo_surface_destroy(cs) end
	if cr == nil then cairo_destroy(cr) end
	local w = conky_window.width
	local h = conky_window.height
	local v = vindsl_hack_height
	local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
	local cr = cairo_create(cs)
	
	cairo_move_to(cr,corner_r,0)
	cairo_line_to(cr,w-corner_r,0)
	cairo_curve_to(cr,w,0,w,0,w,corner_r)
	cairo_line_to(cr,w,h+v-corner_r)
	cairo_curve_to(cr,w,h+v,w,h+v,w-corner_r,h+v)
	cairo_line_to(cr,corner_r,h+v)
	cairo_curve_to(cr,0,h+v,0,h+v,0,h+v-corner_r)
	cairo_line_to(cr,0,corner_r)
	cairo_curve_to(cr,0,0,0,0,corner_r,0)
	cairo_close_path(cr)

	cairo_set_source_rgba(cr,rgb_to_r_g_b(bg_colour,bg_alpha))
	cairo_fill(cr)

	cairo_surface_destroy(cs)
	cairo_destroy(cr)
	end


```
Hope this helps

---

### Post by GreatDanton on 2012-07-07
Thank you guys. I have few more problems with adjusting the numbers in one column, but I hope I will do that till the next week. 

After that I will need forum moderator, because I will post the whole solution here, but someone has to reorganize thread (delete unused posts, etc...)

Thank you for all your help.

---

### Post by GreatDanton on 2012-07-07
here is the update. Take a look at the attachments. In few days I will finish it (help me).

The second line in the temperature code has to change. I cannot use the same trick like in the third and fourth line (with cut command).
```
#######################
#    TEMPERATURE      #  by Great Danton
#######################

${font DroidSans:size=8:weight=bold}${color4}TEMPERATURE  ${color8}${hr 2}$color
${font DroidSans:size=8.65}${color3}CPU FAN Speed${exec sensors | grep "CPU" | awk -F "(" '{print $1}' | cut -c7- }
${font DroidSans:size=8.65}${color3}MB Temperature${offset 105}${exec sensors | grep "MB " | awk -F "(" '{print $1}' | cut -c16- }
${font DroidSans:size=8.65}${color3}Graphic card${offset 120}${exec sensors | grep "temp1" | cut -c7-}
```

---

### Post by sandyd on 2012-07-07
```
#######################
#    TEMPERATURE      #  by Great Danton
#######################

${font DroidSans:size=8:weight=bold}${color4}TEMPERATURE  ${color8}${hr 2}$color
${font DroidSans:size=8.65}${color3}CPU FAN Speed${exec sensors | grep "CPU FAN Speed" | awk -F "(" '{print $1}' | cut -c21- }
${font DroidSans:size=8.65}${color3}MB Temperature${offset 105}${exec sensors | grep "MB " | awk -F "(" '{print $1}' | cut -c16- }
${font DroidSans:size=8.65}${color3}Graphic card${offset 120}${exec sensors | grep "temp1" | cut -c7-}
```

---

### Post by GreatDanton on 2012-07-07
few adjustments needed for the weather section (the temperatures of the bottom)

---

### Post by GreatDanton on 2012-07-08
The conky is finally finished. Yay! I spend almost a week to align all things to the right places.

First I would like to thank all people who helped me. In the first place that are Ubuntu members: Quackers, and sandyd. Especially I would like to thank sandyd who helped me with the temperature section. I wrote the code, and she corrected this code for me. Without her I would not be able to represent you this beautiful conky today. After her here comes Quackers, who took his spare time, to answer at my questions. I would like to thank him for all his patience.

I would also like to mention Gillingham who was the first one who helped me with the errors I had.

Thank you all, because without you I wouldn't be able to write this text here.

**At last I would like to thank the creator of this awesome conky and that is VinDSL. Thank you for creating this amazing conky script.**

Also I would like to mention 42dorian. He is the one who wrote this amazing tutorial at this site here:[http://ubuntuforums.org/showthread.php?p=10879356#post10879356](http://ubuntuforums.org/showthread.php?p=10879356#post10879356). I forgot to add him in this post, before it was edited, so I add him now. 42dorian, I am really sorry for this, even if you said it's okay. I didn't want to do that, but nobody mentioned me this.

The reason why I delete my instructions was because now I understand why everyone, who would like to have conky, should read the tutorial on the link I provided before. After that tutorial you will understand what is really going behind conky, and how to solve your problems alone. I know it's hard for beginner (I am still, but now I know much more then before), but if you want a conky - then you should make something in this way.

Once again here is the link which you should use in order to make your conky working:[http://ubuntuforums.org/showthread.php?t=1771033](http://ubuntuforums.org/showthread.php?t=1771033)

My resolution is **1920x1080**, so if you have less y pixels, you will not be able to have all informations like me. Keep in mind that I am not coder, therefore I got this results with experiments.


> Other things you will need, in order to make your Conky work:

1) .conkyrc (The actual conky script.)
2) draw_bg.lua (That shaded area around his script)
3) bargraph_small.lua (This puts all of the usage bars next to his CPU and Memory objects.)
4) vindsl-rangaloo-google-weather-2.0.zip, his weather method (explained in another thread.) &#8594; get this at this site: [http://ubuntuforums.org/showthread.php?t=1771033](http://ubuntuforums.org/showthread.php?t=1771033).
5) Place it in the .conky folder in: /home/yourusername/
6) conky-start-delayed.sh (This delays when startup runs Conky so that it doesn't interfere with your other windows. This is sometimes tweaked substantially depending on what Window Manager you're using.) &#8594; **I will not have this in my post, because I don't use it. If you want that script go to the previous link.**

And now finally conky:
[B]At this time I have conky 1.9-which places conky folder in:
/etc/conky/conky.conf)[/B] IF you have different version of conky then your conky folder might be in the other place.

```
# Conky, a system monitor, based on torsmo
#
# Any original torsmo code is licensed under the BSD license
#
# All code written since the fork of torsmo is licensed under the GPL
#
# Please see COPYING for details
#
# Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
# Copyright (c) 2005-2010 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
# All rights reserved.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

# Conky configuration
alignment top_right
background yes
##################################
## VinDSL | rev. 11-12-01 20:20 ## modified by GreatDanton 8.7.2012
##################################
##     December 2011 Series     ##
##################################

## ¡PLEASE READ THE FINE PRINT! ##

####
## Development Platforms (current)
#
#  Ubuntu 10.10 'Maverick Meerkat' (GNOME 2.28 - Conky 1.8.0)
#  Ubuntu 12.04 'Precise Pangolin' (GNOME-SHELL - UNITY 2D/3D - Conky 1.8.1)
#  Screen Resolution: 1920x1080 (Samsung Syncmaster S24B300B)

####
## Prerequisites (required)
#
#  conky-all 1.8.0 or 1.8.1-5
#  cURL - Command Line Tool
#  xsltproc - Command Line Tool
#  UTF-8 Compatible Text Editor
#
## Tips n' Tricks
## Several ppl (including myself) have experienced issues with conky-all 1.8.1-6
## In every instance, downgrading to conky-all 1.8.1-5 has solved the problem(s).
## I recommend using (and pinning) conky-all 1.8.1-5 until things get sorted.
## conky-all 1.8.1-5 can be downloaded here: https://launchpad.net/ubuntu/+source/conky-all/1.8.1-5

####
## Installed fonts (required)
#
#  ConkyWeather (Stanko Metodiev)
#  Cut Outs for 3D FX (Fonts & Things)
#  Droid Font Family (Google Android SDK)
#  KR A Round (Kat's Fun Fonts)
#  OpenLogos (Icoma)
#  PizzaDude Bullets (Jakob Fischer)
#  Radio Space (Iconian Fonts)
#  StyleBats (Vinterstille)
#  Ubuntu Font Family (Canonical Ltd)
#  Ubuntu Title Bold (Paulo Silva - not included in link below)
#  Weather (Jonathan Macagba)
# 
## Tips n' Tricks from Mr. Peachy, djyoung4, and 42dorian (Thanks!)
## Most necessary fonts can be downloaded here: http://ompldr.org/vOHdoag
## Unzip the fonts into your font folder, for example: /home/username/.fonts
## Run this command in a terminal (rebuilds font cache file): sudo fc-cache -fv

####
## Use XFT? Required to Force UTF8 (see below)
#
use_xft yes
xftfont DroidSans:size=8.75
xftalpha 0.1

####
## Force UTF8? Requires XFT (see above)
## Displays degree symbol, instead of Â°, etc.
#
override_utf8_locale yes

####
## This buffer is used for text, single lines, output from $exec, and other variables.
## Increasing the text buffer size (too high) will drastically reduce Conky's performance.
## Decreasing the size (too low) will truncate content and cause strange display output.
## Standard text buffer size is 256 bytes (cannot be less). Adjust YOUR buffer wisely!
#
text_buffer_size 640

####
## Daemonize Conky, aka 'fork to background'.
#
background yes

####
## Update interval in seconds.
#
update_interval 2.0

####
## The number of times Conky will update before quitting.
## Zero makes Conky run forever.
#
total_run_times 0

####
## Create own window in instead of using desktop?
#
own_window yes
own_window_transparent yes
own_window_type normal
own_window_class conky-semi
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
####
## Some distros also require the following 2 lines.
#
own_window_argb_visual yes
own_window_argb_value 255

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
draw_shades yes
default_shade_color 292421

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
## Minimum size of the text area.
## Syntax: minimum_size [width] [height]
#
minimum_size 240 1394

####
## Maximum width of the text area.
## Syntax: maximum_width [width]
#
maximum_width 255

####
## Gap between text and screen borders.
#
gap_x 6	  ## Left / Right
gap_y 32  ## Top / Bottom

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
## My colors (suit yourself)
#
color0 White		#FFFFFF
color1 Ivory		#FFFFF0
color2 Ivory2		#EEEEE0
color3 Ivory3		#CDCDC1
color4 Tan1		#FFA54F
color5 Tan2		#EE9A49
color6 Gray		#7E7E7E
color7 AntiqueWhite4	#8B8378
color8 DimGray		#696969
color9 Tomato		#FF6347

#####
## Load Lua for shading (optional)
## Set the path to your script here.
#
lua_load ~/.conky/draw_bg.lua
lua_draw_hook_pre draw_bg

####
## Load Lua for bargraphs (required)
## Set the path to your script here.
#
lua_load ~/.conky/bargraph_small.lua
lua_draw_hook_post main_bars

TEXT
##################################
##             LOGO             ##
##################################
## Uncomment for hard-coded ID (static)
#${voffset -33}${font OpenLogos:size=103}${color2}v${font}${voffset -76}${goto 179}${font UbuntuTitleBold:size=19.6}${color4}1${offset 1}2${offset 1}.${offset 0}0${offset 0}4${font}
####
## Uncomment for soft-coded ID (dynamic)
${voffset -33}${font OpenLogos:size=103}${color2}v${font}${voffset -76}${goto 179}${font UbuntuTitleBold:size=19.6}${color4}${pre_exec cat /etc/*release | grep 'RELEASE' | awk -F'=' '{print $2}'}${font}
####
## Additional ID (branch version, code name, release date, etc.)
${voffset -1}${goto 188}${font Ubuntu-B:size=7}${color4}Precise Pangolin${font}
##################################
##            SYSTEM            ##
##################################
${voffset 7}${font DroidSans:bold:size=8.25}${color4}SYSTEM${offset 8}${color8}${voffset -2}${hr 2}${font}
# ${voffset 4}${font OpenLogos:size=10}${color2}u${voffset -4}${font DroidSans:size=8.6}${color3}${offset 5}${pre_exec lsb_release -sd || cat /etc/*release}${font}
${voffset 2}${offset -2}${font OpenLogos:size=12}${color2}Z${voffset -4}${font DroidSans:size=8.6}${color3}${offset 3}${sysname}${offset 3}${kernel}${alignr}${font DroidSans:size=8.3}${machine}${font}
${voffset 2}${font StyleBats:size=10}${color2}d${voffset -2}${font DroidSans:size=8.6}${color3}${offset 5}ATI Radeon HD 4800${alignr}${font DroidSans:size=8.3}
${voffset 2}${font StyleBats:size=10}${color2}A${voffset -1}${font DroidSans:size=8.6}${color3}${offset 5}Intel${offset 3}Core™2 Duo${offset 3}CPU${offset 3}E6850${alignr 1}${font DroidSans:size=8.3}${freq_g cpu0}${offset 1}GHz${font}
${voffset 2}${font StyleBats:size=10}${color2}q${voffset -1}${font DroidSans:size=8.6}${color3}${offset 5}System${offset 3}Uptime${alignr}${font DroidSans:size=8.3}${uptime_short}${font}
##################################
##          PROCESSORS          ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}PROCESSORS${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=9.9}${color2}k${voffset -2}${font DroidSansFallback:size=8.39}${color3}${offset 2}CPU1${offset 5}${font DroidSans:size=8.3}${cpu cpu1}%${font}
${voffset 2}${font StyleBats:size=9.9}${color2}k${voffset -2}${font DroidSansFallback:size=8.39}${color3}${offset 2}CPU2${offset 5}${font DroidSans:size=8.3}${cpu cpu2}%${font}
##################################
##            MEMORY            ##
##################################
${voffset 5}${font DroidSans:bold:size=8}${color4}MEMORY${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=10}${color2}l${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 3}RAM${goto 97}${font DroidSans:size=8.3}${mem}${goto 133}/${offset 5}${memmax}${alignr}${memperc}%${font}
##################################
##             HDD              ##
##################################
${voffset 15}${font DroidSans:bold:size=8}${color4}HDD${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 6}${font StyleBats:size=9.9}${color2}x${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}ROOT${goto 95}${font DroidSans:size=8.3}${fs_used /}${goto 133}/${offset 5}${fs_size /}${alignr}${fs_free_perc /}%${font}
${voffset 15}${font StyleBats:size=9.9}${color2}x${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}HOME${goto 95}${font DroidSans:size=8.3}${fs_used /home}${goto 133}/${offset 5}${fs_size /home}${alignr}${fs_free_perc /home}%${font}
${voffset 15}${font StyleBats:size=9.9}${color2}4${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}SWAP${goto 95}${font DroidSans:size=8.3}${swap}${goto 133}/${offset 5}${swapmax}${alignr}${swapperc}%${font}

#######################
#    TEMPERATURE      #  by Sandyd & GreatDanton
#######################

${font DroidSans:size=8:weight=bold}${color4}TEMPERATURE  ${color8}${hr 2}$color
${font DroidSans:size=8.65}${color3}CPU FAN Speed${offset 123}${exec sensors | grep "CPU FAN Speed" | awk -F "(" '{print $1}' | cut -c21- }
${font DroidSans:size=8.65}${color3}CPU Temperature${offset 123}${exec sensors | grep "CPU Temperature" |  awk -F "(" '{print $1}' | cut -c22-}
${font DroidSans:size=8.65}${color3}MB Temperature${offset 110}${exec sensors | grep "MB " | awk -F "(" '{print $1}' | cut -c16- }
${font DroidSans:size=8.65}${color3}Graphic card${offset 125}${exec sensors | grep "temp1" | cut -c7-}
##################################
##         TOP PROCESSES        ##
##################################
${voffset 15}${font DroidSans:bold:size=8}${color4}TOP PROCESSES${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 6}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 1}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 1}${alignr}${top_mem mem 1}%${font}
${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 2}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 2}${alignr}${top_mem mem 2}%${font}
${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 3}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 3}${alignr}${top_mem mem 3}%${font}
${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 4}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 4}${alignr}${top_mem mem 4}%${font}
${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 5}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 5}${alignr}${top_mem mem 5}%${font}
# ${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 6}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 6}${alignr}${top_mem mem 6}%${font}
##################################
##           NETWORK            ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}NETWORK${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font PizzaDudeBullets:size=9.5}${color6}T${font DroidSans:size=8.65}${color3}${offset 5}Download${goto 120}${font DroidSans:size=8.3}${totaldown wlan0}${alignr}${font DroidSans:size=8.3}${downspeed wlan0}${font}
${voffset 0}${font PizzaDudeBullets:size=9.5}${color6}N${font DroidSans:size=8.65}${color3}${offset 5}Upload${goto 120}${font DroidSans:size=8.3}${totalup wlan0}${alignr}${font DroidSans:size=8.3}${upspeed wlan0}${font}
#${voffset 4}${font PizzaDudeBullets:size=9.5}${color6}a${font DroidSans:size=8.65}${color3}${offset 5}Private${offset 3}IP${goto 123}#${font DroidSansFallback:size=8.5}LAN${alignr}${font DroidSans:size=8.3}${addr wlan0}${font}
#${voffset 0}${font PizzaDudeBullets:size=9.5}${color6}a${font DroidSans:size=8.65}${color3}${offset 5}Public${offset 7}IP${goto 121}#${font DroidSansFallback:size=8.5}WAN${alignr}${font DroidSans:size=8.3}${execi 1800 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}${font}
##################################
##     WEATHER (Imperial)       ##
##################################
#${voffset 4}${font DroidSans:bold:size=8.25}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
#${voffset -55}${font RadioSpace:size=34}${color3}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" ctbi}${font}${voffset -28}#${goto 33}${font Weather:size=42}${color3}y${font}
#${voffset -38}${font Ubuntu:size=8.63}${color5}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" ctti}${font}
#${voffset -39}${font KRARound:size=36}${color3}${goto 195}I${font}
#${voffset 6}${font Ubuntu:size=23}${color5}${alignc -2}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" ccb}${font}
#${voffset 8}${font DroidSansFallback:size=8.63}${color3}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ"}${font}
#${voffset -57}${font ConkyWeather:size=48}${color6}${alignc -55}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" cp}${font}
#${voffset 6}${font DroidSansMono:bold:size=8.62}${color4}${offset 40}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" dl}#${font}
#${voffset 0}${font ConkyWeather:size=37.9}${color3}${offset 26}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" fcp}${font}
#${voffset 0}${font DroidSansFallback:bold:size=8.62}${color4}${offset 28}${execi 1800 /home/jan/.conky/weather/weather.sh "Scottsdale,AZ" fcti}${font}
##################################
##      WEATHER (Metric)        ##
##################################
${voffset 4}${font DroidSans:bold:size=8.25}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
${goto 70}${font RadioSpace:size=34}${color3}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" ctbm}${font}${voffset -28}${goto 33}${font Weather:size=42}${color3}y${font}
${voffset -39}${font Ubuntu:size=8.63}${color5}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" cttm}${font}
${font KRARound:size=36}${color3}${voffset -38}${goto 195}I${font}
${voffset 6}${font Ubuntu:size=23}${color5}${alignc -2}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" ccb}${font}
${voffset 8}${font DroidSansFallback:size=8.63}${color3}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana"}${font}
${voffset -57}${font ConkyWeather:size=48}${color6}${alignc -55}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" cp}${font}
${voffset 6}${font DroidSansMono:bold:size=8.62}${color4}${offset 40}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" dl}${font}
${voffset 0}${font ConkyWeather:size=37.9}${color3}${offset 26}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" fcp}${font}
${voffset 0}${font DroidSansFallback:bold:size=8.62}${color4}${offset 26}${execi 1800 /home/jan/.conky/weather/weather.sh "Ljubljana" fctm}${font}
##################################
##             TIME             ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}TIME${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset -4}${font RadioSpace:size=32}${color3}${if_match ${time %l}<=9}${alignc 7}${time %l:%M%p}${else}${if_match ${time %l}>=10}${alignc -1}${time %l:%M%p}${endif}${endif}${font}
##################################
##      CALENDAR (5-Line)       ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}DATE${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 18}${font DroidSansMono:size=7.55}${color3}${alignc 60}${time %A}${font}
${voffset -4}${font DroidSansFallback:bold:size=18}${if_match ${time %e}<=9}${color5}${alignc 65}${time %e}${font}${else}${if_match ${time %e}>=10}${color5}${alignc 60}${time %e}${endif}${endif}${font}
${voffset 0}${font DroidSansMono:size=7.55}${color3}${alignc 60}${time %B}${font}
${voffset 0}${font DroidSansMono:size=7.6}${color3}${alignc 60}${time %Y}${font}
${voffset -83}${font CutOutsFor3DFX:size=67}${color8}${alignc 99}2${font}
####
## Uncomment for Conky 1.8.0 (use mono fonts only)
# ${voffset -68}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_9=`date +%-d`; ncal -M -C -h | sed -e 's/\r//g' -e 's/^/ /g' -e '1d' -e 's/\<'"$VinDSL_Cal_9"'\>/${color4}&${color3}/'}
####
## Uncomment for Conky 1.8.1 (use mono fonts only)
${voffset -64}${offset 0}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_9=`date +%-d`; ncal -M -C -h | sed -e 's/\r//g' -e 's/^/                    /g' -e '1d' -e 's/\<'"$VinDSL_Cal_9"'\>/${color4}&${color3}/'}

##################################
##   RHYTHMBOX (Experimental)   ##
##################################
#${if_running rhythmbox}
#${voffset -8}${font DroidSans:bold:size=7.75}${color4}RHYTHMBOX${offset 8}${color8}${voffset -2}${hr 2}${font}
#${voffset 8}${font DroidSans:size=8.25}${color3}${if_match "${execpi 2 expr length "`/usr/bin/rhythmbox-client --print-playing-format %tt | head -n 1`"}" >= "48"}${alignr 15}${scroll 38 4* #${execi 2 rhythmbox-client --print-playing-format %tt --no-start}}${font}${else}${alignc}${execi 2 rhythmbox-client --print-playing-format %tt --no-start}${font}${endif}${endif}

```

---

### Post by GreatDanton on 2012-07-08
bargraph_small.lua
~/home/username/.conky/bargraph_small.lua

```
--[[
BARGRAPH WIDGET
v2.1 by wlourf (07 Jan. 2011)
this widget draws a bargraph with different effects 
http://u-scripts.blogspot.com/2010/07/bargraph-widget.html
	
To call the script in a conky, use, before TEXT
	lua_load /path/to/the/script/bargraph.lua
	lua_draw_hook_pre main_rings
and add one line (blank or not) after TEXT
	
Parameters are :
3 parameters are mandatory
name - the name of the conky variable to display, for example for {$cpu cpu0}, just write name="cpu"
arg  - the argument of the above variable, for example for {$cpu cpu0}, just write arg="cpu0"
       arg can be a numerical value if name=""
max  - the maximum value the above variable can reach, for example, for {$cpu cpu0}, just write max=100
	
Optional parameters:
x,y	  - coordinates of the starting point of the bar, default = middle of the conky window
cap	  - end of cap line, ossibles values are r,b,s (for round, butt, square), default="b"
	    http://www.cairographics.org/samples/set_line_cap/
angle	  - angle of rotation of the bar in degress, default = 0 (i.e. a vertical bar)
	    set to 90 for an horizontal bar
skew_x	  - skew bar around x axis, default = 0
skew_y	  - skew bar around y axis, default = 0
blocks    - number of blocks to display for a bar (values >0) , default= 10
height	  - height of a block, default=10 pixels
width	  - width of a block, default=20 pixels
space	  - space between 2 blocks, default=2 pixels
angle_bar - this angle is used to draw a bar on a circular way (ok, this is no more a bar !) default=0
radius	  - for cicular bars, internal radius, default=0
	    with radius, parameter width has no more effect.

Colours below are defined into braces {colour in hexadecimal, alpha}
fg_colour    - colour of a block ON, default= {0x00FF00,1}
bg_colour    - colour of a block OFF, default = {0x00FF00,0.5}
alarm	     - threshold, values after this threshold will use alarm_colour colour , default=max
alarm_colour - colour of a block greater than alarm, default=fg_colour
smooth	     - (true or false), create a gradient from fg_colour to bg_colour, default=false 
mid_colour   - colours to add to gradient, with this syntax {position into the gradient (0 to1), colour hexa, alpha}
	       for example, this table {{0.25,0xff0000,1},{0.5,0x00ff00,1},{0.75,0x0000ff,1}} will add
	       3 colours to gradient created by fg_colour and alarm_colour, default=no mid_colour
led_effect   - add LED effects to each block, default=no led_effect
	       if smooth=true, led_effect is not used
	       possibles values : "r","a","e" for radial, parallel, perdendicular to the bar (just try!)
	       led_effect has to be used with theses colours :
fg_led	     - middle colour of a block ON, default = fg_colour
bg_led	     - middle colour of a block OFF, default = bg_colour
alarm_led    - middle colour of a block > ALARM,  default = alarm_colour

reflection parameters, not available for circular bars
reflection_alpha  - add a reflection effect (values from 0 to 1) default = 0 = no reflection
		    other values = starting opacity
reflection_scale  - scale of the reflection (default = 1 = height of text)
reflection_length - length of reflection, define where the opacity will be set to zero
		    values from 0 to 1, default =1
reflection	  - position of reflection, relative to a vertical bar, default="b"
		    possibles values are : "b","t","l","r" for bottom, top, left, right
draw_me     	  - if set to false, text is not drawn (default = true or 1)
		    it can be used with a conky string, if the string returns 1, the text is drawn :
		    example : "${if_empty ${wireless_essid wlan0}}${else}1$endif",

v1.0 (10 Feb. 2010) original release
v1.1 (13 Feb. 2010) numeric values can be passed instead conky stats with parameters name="", arg = numeric_value	
v1.2 (28 Feb. 2010) just renamed the widget to bargraph
v1.3 (03 Mar. 2010) added parameters radius & angle_bar to draw the bar in a circular way
v2.0 (12 Jul. 2010) rewrite script + add reflection effects and parameters are now set into tables
v2.1 (07 Jan. 2011) Add draw_me parameter and correct memory leaks, thanks to "Creamy Goodness"

--      This program is free software; you can redistribute it and/or modify
--      it under the terms of the GNU General Public License as published by
--      the Free Software Foundation version 3 (GPLv3)
--     
--      This program is distributed in the hope that it will be useful,
--      but WITHOUT ANY WARRANTY; without even the implied warranty of
--      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
--      GNU General Public License for more details.
--     
--      You should have received a copy of the GNU General Public License
--      along with this program; if not, write to the Free Software
--      Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
--      MA 02110-1301, USA.		

]]

require 'cairo'

----------------START OF PARAMETERS ----------
function conky_main_bars()
	local bars_settings={
		{	--[ Graph for CPU1 ]--
			name="cpu",
			arg="cpu1",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=82,y=156,
			blocks=55,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},
		{	--[ Graph for CPU2 ]--
			name="cpu",
			arg="cpu2",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=82,y=170,
			blocks=55,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},
		{	--[ Graph for Memory ]--
			name="memperc",
			arg="",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=15,y=220,
			blocks=77,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},
		{	--[ Graph for Root ]--
                        name="fs_used_perc",
			arg="/",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=15,y=267,
			blocks=77,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},	
		{	--[ Graph for Home ]--
			name="fs_used_perc",
			arg="/home",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=15,y=295,
			blocks=77,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},	
	        {	--[ Graph for Swap ]--
                        name="swapperc",
			arg="",
			max=100,
			alarm=50,
			alarm_colour={0xFF0000,0.72},
			bg_colour={0xFFFFFF,0.25},
			fg_colour={0x00FF00,0.55},
			mid_colour={{0.45,0xFFFF00,0.70}},
			x=15,y=323,
			blocks=77,
			space=1,
			height=2,width=5,
			angle=90,
			smooth=true
			},
		 }	
-----------END OF PARAMETERS--------------


    
	if conky_window == nil then return end
	
	local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
	
	cr = cairo_create(cs)    
	--prevent segmentation error when reading cpu state
    if tonumber(conky_parse('${updates}'))>3 then
        for i in pairs(bars_settings) do
        	
        	draw_multi_bar_graph(bars_settings[i])
        	
        end
    end
	cairo_destroy(cr)
	cairo_surface_destroy(cs)
	cr=nil

end



function draw_multi_bar_graph(t)
	cairo_save(cr)
	--check values
	if t.draw_me == true then t.draw_me = nil end
	if t.draw_me ~= nil and conky_parse(tostring(t.draw_me)) ~= "1" then return end	
	if t.name==nil and t.arg==nil then 
		print ("No input values ... use parameters 'name' with 'arg' or only parameter 'arg' ") 
		return
	end
	if t.max==nil then
		print ("No maximum value defined, use 'max'")
		return
	end
	if t.name==nil then t.name="" end
	if t.arg==nil then t.arg="" end

	--set default values	
	if t.x == nil		then t.x = conky_window.width/2 end
	if t.y == nil		then t.y = conky_window.height/2 end
	if t.blocks == nil	then t.blocks=10 end
	if t.height == nil	then t.height=10 end
	if t.angle == nil 	then t.angle=0 end
	t.angle = t.angle*math.pi/180
	--line cap style
	if t.cap==nil		then t.cap = "b" end
	local cap="b"
	for i,v in ipairs({"s","r","b"}) do 
		if v==t.cap then cap=v end
	end
	local delta=0
	if t.cap=="r" or t.cap=="s" then delta = t.height end
	if cap=="s" then 	cap = CAIRO_LINE_CAP_SQUARE
	elseif cap=="r" then
		cap = CAIRO_LINE_CAP_ROUND
	elseif cap=="b" then
		cap = CAIRO_LINE_CAP_BUTT
	end
	--end line cap style
	--if t.led_effect == nil	then t.led_effect="r" end
	if t.width == nil	then t.width=20 end
	if t.space == nil	then t.space=2 end
	if t.radius == nil	then t.radius=0 end
	if t.angle_bar == nil	then t.angle_bar=0 end
	t.angle_bar = t.angle_bar*math.pi/360 --halt angle
	
	--colours
	if t.bg_colour == nil 	then t.bg_colour = {0x00FF00,0.5} end
	if #t.bg_colour~=2 		then t.bg_colour = {0x00FF00,0.5} end
	if t.fg_colour == nil 	then t.fg_colour = {0x00FF00,1} end
	if #t.fg_colour~=2 		then t.fg_colour = {0x00FF00,1} end
	if t.alarm_colour == nil 	then t.alarm_colour = t.fg_colour end
	if #t.alarm_colour~=2 		then t.alarm_colour = t.fg_colour end

	if t.mid_colour ~= nil then	
		for i=1, #t.mid_colour do    
		    if #t.mid_colour[i]~=3 then 
		    	print ("error in mid_color table")
		    	t.mid_colour[i]={1,0xFFFFFF,1} 
		    end
		end
    end
    
	if t.bg_led ~= nil and #t.bg_led~=2	then t.bg_led = t.bg_colour end
	if t.fg_led ~= nil and #t.fg_led~=2	then t.fg_led = t.fg_colour end
	if t.alarm_led~= nil and #t.alarm_led~=2 then t.alarm_led = t.fg_led end
	
	if t.led_effect~=nil then
		if t.bg_led == nil then t.bg_led = t.bg_colour end
		if t.fg_led == nil 	then t.fg_led = t.fg_colour end
		if t.alarm_led == nil  then t.alarm_led = t.fg_led end
	end
	

	if t.alarm==nil then t.alarm = t.max end --0.8*t.max end
	if t.smooth == nil then t.smooth = false end

	if t.skew_x == nil then 
		t.skew_x=0 
	else
		t.skew_x = math.pi*t.skew_x/180	
	end
	if t.skew_y == nil then 
		t.skew_y=0
	else
		t.skew_y = math.pi*t.skew_y/180	
	end
	
	if t.reflection_alpha==nil then t.reflection_alpha=0 end
	if t.reflection_length==nil then t.reflection_length=1 end
	if t.reflection_scale==nil then t.reflection_scale=1 end
	
	--end of default values
	

 	local function rgb_to_r_g_b(col_a)
		return ((col_a[1] / 0x10000) % 0x100) / 255., ((col_a[1] / 0x100) % 0x100) / 255., (col_a[1] % 0x100) / 255., col_a[2]
	end
	
	
	--functions used to create patterns

	local function create_smooth_linear_gradient(x0,y0,x1,y1)
		local pat = cairo_pattern_create_linear (x0,y0,x1,y1)
		cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(t.fg_colour))
		cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(t.alarm_colour))
		if t.mid_colour ~=nil then
			for i=1, #t.mid_colour do
				cairo_pattern_add_color_stop_rgba (pat, t.mid_colour[i][1], rgb_to_r_g_b({t.mid_colour[i][2],t.mid_colour[i][3]}))
			end
		end
		return pat
	end

	local function create_smooth_radial_gradient(x0,y0,r0,x1,y1,r1)
		local pat =  cairo_pattern_create_radial (x0,y0,r0,x1,y1,r1)
		cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(t.fg_colour))
		cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(t.alarm_colour))
		if t.mid_colour ~=nil then
			for i=1, #t.mid_colour do
				cairo_pattern_add_color_stop_rgba (pat, t.mid_colour[i][1], rgb_to_r_g_b({t.mid_colour[i][2],t.mid_colour[i][3]}))
			end
		end
		return pat
	end
	
	local function create_led_linear_gradient(x0,y0,x1,y1,col_alp,col_led)
		local pat = cairo_pattern_create_linear (x0,y0,x1,y1) ---delta, 0,delta+ t.width,0)
		cairo_pattern_add_color_stop_rgba (pat, 0.0, rgb_to_r_g_b(col_alp))
		cairo_pattern_add_color_stop_rgba (pat, 0.5, rgb_to_r_g_b(col_led))
		cairo_pattern_add_color_stop_rgba (pat, 1.0, rgb_to_r_g_b(col_alp))
		return pat
	end

	local function create_led_radial_gradient(x0,y0,r0,x1,y1,r1,col_alp,col_led,mode)
		local pat = cairo_pattern_create_radial (x0,y0,r0,x1,y1,r1)
		if mode==3 then
			cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(col_alp))				
			cairo_pattern_add_color_stop_rgba (pat, 0.5, rgb_to_r_g_b(col_led))
			cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(col_alp))				
		else
			cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(col_led))
			cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(col_alp))				
		end
		return pat
	end






	local function draw_single_bar()
		--this fucntion is used for bars with a single block (blocks=1) but 
		--the drawing is cut in 3 blocks : value/alarm/background
		--not zvzimzblr for circular bar
		local function create_pattern(col_alp,col_led,bg)
			local pat
			
			if not t.smooth then
				if t.led_effect=="e" then
					pat = create_led_linear_gradient (-delta, 0,delta+ t.width,0,col_alp,col_led)
				elseif t.led_effect=="a" then
					pat = create_led_linear_gradient (t.width/2, 0,t.width/2,-t.height,col_alp,col_led)
				elseif  t.led_effect=="r" then
					pat = create_led_radial_gradient (t.width/2, -t.height/2, 0, t.width/2,-t.height/2,t.height/1.5,col_alp,col_led,2)
				else
					pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(col_alp))
				end
			else
				if bg then
					pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(t.bg_colour))
				else
					pat = create_smooth_linear_gradient(t.width/2, 0, t.width/2,-t.height)
				end
			end
			return pat
		end
		
		local y1=-t.height*pct/100
		local y2,y3
		if pct>(100*t.alarm/t.max) then 
			y1 = -t.height*t.alarm/100
			y2 = -t.height*pct/100
			if t.smooth then y1=y2 end
		end
		
		if t.angle_bar==0 then
		
			--block for fg value
			local pat = create_pattern(t.fg_colour,t.fg_led,false)
			cairo_set_source(cr,pat)
			cairo_rectangle(cr,0,0,t.width,y1)
			cairo_fill(cr)
			cairo_pattern_destroy(pat)
		
			-- block for alarm value			
			if not t.smooth and y2 ~=nil then 
				pat = create_pattern(t.alarm_colour,t.alarm_led,false)
				cairo_set_source(cr,pat)
				cairo_rectangle(cr,0,y1,t.width,y2-y1)
				cairo_fill(cr)
				y3=y2
				cairo_pattern_destroy(pat)
			else
				y2,y3=y1,y1
			end
			-- block for bg value
			cairo_rectangle(cr,0,y2,t.width,-t.height-y3)
			pat = create_pattern(t.bg_colour,t.bg_led,true)
			cairo_set_source(cr,pat)
			cairo_pattern_destroy(pat)
			cairo_fill(cr)
		end		
	end  --end single bar
	





	local function draw_multi_bar()
		--function used for bars with 2 or more blocks
		for pt = 1,t.blocks do 
			--set block y
			local y1 = -(pt-1)*(t.height+t.space)
			local light_on=false
			
			--set colors
			local col_alp = t.bg_colour
			local col_led = t.bg_led
			if pct>=(100/t.blocks) or pct>0 then --ligth on or not the block
				if pct>=(pcb*(pt-1))  then 
					light_on = true
					col_alp = t.fg_colour
					col_led = t.fg_led
					if pct>=(100*t.alarm/t.max) and (pcb*pt)>(100*t.alarm/t.max) then 
						col_alp = t.alarm_colour 
						col_led = t.alarm_led 
					end
				end
			end

			--set colors
			--have to try to create gradients outside the loop ?
			local pat 
			
			if not t.smooth then
				if t.angle_bar==0 then
					if t.led_effect=="e" then
						pat = create_led_linear_gradient (-delta, 0,delta+ t.width,0,col_alp,col_led)
					elseif t.led_effect=="a" then
						pat = create_led_linear_gradient (t.width/2, -t.height/2+y1,t.width/2,0+t.height/2+y1,col_alp,col_led)					
					elseif  t.led_effect=="r" then
						pat = create_led_radial_gradient (t.width/2, y1, 0, t.width/2,y1,t.width/1.5,col_alp,col_led,2)	
					else
						pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(col_alp))
					end
				else
					 if t.led_effect=="a"  then
						 pat = create_led_radial_gradient (0, 0, t.radius+(t.height+t.space)*(pt-1),
														 0, 0, t.radius+(t.height+t.space)*(pt),						 
											 col_alp,col_led,3)	
					else
						pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(col_alp))					
					end
					
				end
			else
				
				if light_on then
					if t.angle_bar==0 then
						pat = create_smooth_linear_gradient(t.width/2, t.height/2, t.width/2,-(t.blocks-0.5)*(t.height+t.space))
					else
						pat = create_smooth_radial_gradient(0, 0, (t.height+t.space),  0,0,(t.blocks+1)*(t.height+t.space),2)
					end
				else		
					pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(t.bg_colour))
				end
			end
			cairo_set_source (cr, pat)
			cairo_pattern_destroy(pat)

			--draw a block
			if t.angle_bar==0 then
				cairo_move_to(cr,0,y1)
				cairo_line_to(cr,t.width,y1)
			else		
				cairo_arc( cr,0,0,
					t.radius+(t.height+t.space)*(pt)-t.height/2,
					 -t.angle_bar -math.pi/2 ,
					 t.angle_bar -math.pi/2)
			end
			cairo_stroke(cr)
		end	
	end
	
	
	
	
	local function setup_bar_graph()
		--function used to retrieve the value to display and to set the cairo structure
		if t.blocks ~=1 then t.y=t.y-t.height/2 end
		
		local value = 0
		if t.name ~="" then
			value = tonumber(conky_parse(string.format('${%s %s}', t.name, t.arg)))
			--$to_bytes doesn't work when value has a decimal point,
			--https://garage.maemo.org/plugins/ggit/browse.php/?p=monky;a=commitdiff;h=174c256c81a027a2ea406f5f37dc036fac0a524b;hp=d75e2db5ed3fc788fb8514121f67316ac3e5f29f
			--http://sourceforge.net/tracker/index.php?func=detail&aid=3000865&group_id=143975&atid=757310
			--conky bug?
			--value = (conky_parse(string.format('${%s %s}', t.name, t.arg)))
			--if string.match(value,"%w") then
			--	value = conky_parse(string.format('${to_bytes %s}',value))
			--end
		else
			value = tonumber(t.arg)
		end

		if value==nil then value =0 end
		
		pct = 100*value/t.max
		pcb = 100/t.blocks
		
		cairo_set_line_width (cr, t.height)
		cairo_set_line_cap  (cr, cap)
		cairo_translate(cr,t.x,t.y)
		cairo_rotate(cr,t.angle)

		local matrix0 = cairo_matrix_t:create()
		tolua.takeownership(matrix0)
		cairo_matrix_init (matrix0, 1,t.skew_y,t.skew_x,1,0,0)
		cairo_transform(cr,matrix0)

	
		
		--call the drawing function for blocks
		if t.blocks==1 and t.angle_bar==0 then
			draw_single_bar()
			if t.reflection=="t" or t.reflection=="b" then cairo_translate(cr,0,-t.height) end
		else
			draw_multi_bar()
		end

		--dot for reminder
		--[[
		if t.blocks ~=1 then
			cairo_set_source_rgba(cr,1,0,0,1)
			cairo_arc(cr,0,t.height/2,3,0,2*math.pi)
			cairo_fill(cr)
		else
			cairo_set_source_rgba(cr,1,0,0,1)
			cairo_arc(cr,0,0,3,0,2*math.pi)
			cairo_fill(cr)
		end]]
		
		--call the drawing function for reflection and prepare the mask used		
		if t.reflection_alpha>0 and t.angle_bar==0 then
			local pat2
			local matrix1 = cairo_matrix_t:create()
			tolua.takeownership(matrix1)
			if t.angle_bar==0 then
				pts={-delta/2,(t.height+t.space)/2,t.width+delta,-(t.height+t.space)*(t.blocks)}
				if t.reflection=="t" then
					cairo_matrix_init (matrix1,1,0,0,-t.reflection_scale,0,-(t.height+t.space)*(t.blocks-0.5)*2*(t.reflection_scale+1)/2)
					pat2 = cairo_pattern_create_linear (t.width/2,-(t.height+t.space)*(t.blocks),t.width/2,(t.height+t.space)/2)
				elseif t.reflection=="r" then
					cairo_matrix_init (matrix1,-t.reflection_scale,0,0,1,delta+2*t.width,0)
					pat2 = cairo_pattern_create_linear (delta/2+t.width,0,-delta/2,0)
				elseif t.reflection=="l" then
					cairo_matrix_init (matrix1,-t.reflection_scale,0,0,1,-delta,0)
					pat2 = cairo_pattern_create_linear (-delta/2,0,delta/2+t.width,-0)
				else --bottom
					cairo_matrix_init (matrix1,1,0,0,-1*t.reflection_scale,0,(t.height+t.space)*(t.reflection_scale+1)/2)
					pat2 = cairo_pattern_create_linear (t.width/2,(t.height+t.space)/2,t.width/2,-(t.height+t.space)*(t.blocks))
				end
			end
			cairo_transform(cr,matrix1)

			if t.blocks==1 and t.angle_bar==0 then
				draw_single_bar()
				cairo_translate(cr,0,-t.height/2) 
			else
				draw_multi_bar()
			end
			
			
			cairo_set_line_width(cr,0.01)
			cairo_pattern_add_color_stop_rgba (pat2, 0,0,0,0,1-t.reflection_alpha)
			cairo_pattern_add_color_stop_rgba (pat2, t.reflection_length,0,0,0,1)
			if t.angle_bar==0 then
				cairo_rectangle(cr,pts[1],pts[2],pts[3],pts[4])
			end
			cairo_clip_preserve(cr)
			cairo_set_operator(cr,CAIRO_OPERATOR_CLEAR)
			cairo_stroke(cr)
			cairo_mask(cr,pat2)
			cairo_pattern_destroy(pat2)
			cairo_set_operator(cr,CAIRO_OPERATOR_OVER)
			
		end --reflection
		pct,pcb=nil
	end --setup_bar_graph()
	
	--start here !
	setup_bar_graph()
	cairo_restore(cr)
end

```

Draw_bg.lua:
~/home/username/.conky/draw_bg.lua

```
--[[	Background by londonali1010 (2009)
	VinDSL Background Hack (2010-2011)

This script draws a background to the Conky window. It covers the whole of the Conky window, but you can specify rounded corners, if you wish.

To call this script in Conky, use (assuming you have saved this script to ~/scripts/):
	lua_load ~/scripts/draw_bg.lua
	lua_draw_hook_pre draw_bg

Changelog:
	+ v3.1	VinDSL Hack (12.01.2011) Added more shading example(s).
	+ v3.0	VinDSL Hack (01.28.2011) Killed memory leak.
	+ v2.4	VinDSL Hack (01.25.2011) Declared all variables in local.
	+ v2.3	VinDSL Hack (12.31.2010) Added shading example(s).
	+ v2.2	VinDSL Hack (12.30.2010) Cleaned up the code a bit.
	+ v2.1	VinDSL Hack (12.24.2010) Added cairo destroy function(s).
	+ v2.0	VinDSL Hack (12.21.2010) Added height adjustment variable.
	+ v1.0	Original release (07.10.2009)

]]

--------------START OF PARAMETERS ------------
-- Change these settings to affect your background:

-- "corner_r" is the radius, in pixels, of the rounded corners. If you don't want rounded corners, use 0.

	local corner_r = 50

-- Set the colour and transparency (alpha) of your background (0.00 - 0.99).

--	(Light Shading Example)
--	local bg_colour = 0x4d4d4d
--	local bg_alpha = 0.50

--	(Medium Shading Example)
--	local bg_colour = 0x222222
--	local bg_alpha = 0.50

--	(Dark Shading Example)
--	local bg_colour = 0x000000
--	local bg_alpha = 0.02

--	(Brown Shading Example)
--	local bg_colour = 0x330000
--	local bg_alpha = 0.04

--	(Ivory Black Shading Example)
--	local bg_colour = 0x292421
--	local bg_alpha = 0.22

--	(Navy Blue Shading Example)
--	local bg_colour = 0x33339F
--	local bg_alpha = 0.33

--	(Olive Green Shading Example)
--	local bg_colour = 0x333319
--	local bg_alpha = 0.13

--	(Silver Shading Example)
	local bg_colour = 0xc0c0c0
	local bg_alpha = 0.05

-- Tweaks the height of your background, in pixels. If you don't need to adjust the height, use 0.

--	(Default Setting)
--	local vindsl_hack_height = 0

	local vindsl_hack_height = -2
---------------END OF PARAMETERS -------------

require 'cairo'
local	cs, cr = nil

local function rgb_to_r_g_b(colour,alpha)
	return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
	end

function conky_draw_bg()
	if conky_window == nil then return end
	if cs == nil then cairo_surface_destroy(cs) end
	if cr == nil then cairo_destroy(cr) end
	local w = conky_window.width
	local h = conky_window.height
	local v = vindsl_hack_height
	local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
	local cr = cairo_create(cs)
	
	cairo_move_to(cr,corner_r,0)
	cairo_line_to(cr,w-corner_r,0)
	cairo_curve_to(cr,w,0,w,0,w,corner_r)
	cairo_line_to(cr,w,h+v-corner_r)
	cairo_curve_to(cr,w,h+v,w,h+v,w-corner_r,h+v)
	cairo_line_to(cr,corner_r,h+v)
	cairo_curve_to(cr,0,h+v,0,h+v,0,h+v-corner_r)
	cairo_line_to(cr,0,corner_r)
	cairo_curve_to(cr,0,0,0,0,corner_r,0)
	cairo_close_path(cr)

	cairo_set_source_rgba(cr,rgb_to_r_g_b(bg_colour,bg_alpha))
	cairo_fill(cr)

	cairo_surface_destroy(cs)
	cairo_destroy(cr)
	end

```

---

### Post by GreatDanton on 2012-07-08
I found this for anyone who want his conky-start delayed


**~/home/username/.config/autostart/conky-start-delayed.sh** (Required - delayed Conky autostart - stops conflicts with Compiz)

```
#!/bin/bash
sleep 60
display=:0.0 conky
```

---

### Post by GreatDanton on 2012-07-08
Here you can download the same weather file as I did.
**WARNING**: I have adjusted only Metric Weather, since I live in Europe. For all who want to use Imperial, just comment (#) $ in Metric Weather and change the numbers {offset} in Imperial Weather. Then you will have temperatures aligned exactly like I have. To adjust you weather to your town/country you have to change "Ljubljana" into the name of your Town. For example if you live in Toronto, you have to change "Ljubljana" into "Toronto"

Remember: After placing weather file (file you have downloaded) in /home/username/.conky open two pictures weather.ttf and weather.otf . After that click on Install button in the bottom right corner. After the installation you will see the pictures in the Weather section.

Keep in mind that if you have different weather script, the conky might not be working. If you have different weather script and the conky is not working, then please don't post questions about it. Like I said before I am not programmer, I make it work by experimenting.

---

### Post by GreatDanton on 2012-07-08
This is all. I hope I didn't forget something important. If I did just let me know and I will try to correct my mistake.

Edit: ooops! I forgot to post the final picture. Here you have it. Enjoy!


[http://ompldr.org/vZW96bg](http://ompldr.org/vZW96bg)

---

### Post by GreatDanton on 2012-07-09
UPDATE 9.7.2012.

VinceDsl contacted me and I asked him how to align the temperatures at the bottom of the Weather section. Here is the solution:
When you download weather file and place it into your /home/username/.conky/weather  folder, you have to adjust some things. It depends of which weather you are using metric or imperial. Since I use **Metric weather** I had to open **fcTemp.Metric.xslt **and made the changes.

Just copy and paste this into your fcTemp.Metric.xslt and you will have aligned the numbers exactly like I have. For those who are interested I highlighted the line where I made the difference. Conky.conf script is already updated, so you don't have to play with numbers.

Keep in mind for those who want to use **Imperial Weather**, you will have to adjust the numbers in conky.conf by yourself. 

Here is the script I am currently using:
```
<!-- fcTemp.Metric.xslt  modified by GreatDanton

This XSLT is used to translate an XML response from the www.google.com/ig/ XML API.

This style sheet shows all HIGH/LOW FORECAST METRIC TEMPS in the Conky Weather Section, e.g.
the high/low metric temperatures that are listed at the bottom of the 3-day forecast.

The first line (forecast day list) in the 3-day forecast is handled by: fcDayList.xslt

The second line (condition icons) in the 3-day forecast is handled by: fcConditions.xslt

Adjust the number of empty spaces (as noted below) to align the horizontal spacing of the
high/low forecast metric temperatures on your desktop.  This works in conjunction with the font
size that you chose to use in your .conkyrc file, and will require some patience to setup.  :)

This is a base adjustment.  Once you get the horizontal alignment into the ballpark, the rest
of the spacing & alignment will be handled, as usual, by making adjustments to the Weather Section
in your .conkyrc file.

NOTE:   ++ Enable the following line, in the weather.sh file, for Metric Stats:

        # cURL the Google Weather API (Metric - Celsius)
        CURLURL="http://www.google.com/ig/api?weather=${LOCID}&hl=en-gb"
-->

<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0" >
    <xsl:output method="text" disable-output-escaping="yes" encoding="utf-8"/>
    <xsl:template match="xml_api_reply">
        <xsl:apply-templates select="weather"/>
    </xsl:template>

    <xsl:template match="weather">
        <xsl:variable name="celsius"><xsl:text>º</xsl:text></xsl:variable><!-- Sets celcius variable / adds degree symbol -->
        <xsl:for-each select="forecast_conditions[position() >= 2 ]"><!-- Selects days, other than today -->
            <xsl:value-of select="high/@data"/> <xsl:value-of select="$celsius"/>
            <xsl:text>/</xsl:text>
            <xsl:value-of select="low/@data"/> <xsl:value-of select="$celsius"/>
                <xsl:if test="position() != 3">
             [COLOR="Red"]       **<xsl:text>        </xsl:text><!-- 11 spaces. Add/subtract spaces for proper Forecast Temperature alignment --><!--I modified (GreatDanton) it to 8 spaces -->**[/COLOR]
                </xsl:if>
        </xsl:for-each>
    </xsl:template>
</xsl:stylesheet>
```

Regards. Also I would recommend you to read all this text. You will understand conky little better, and I won't need to answer as questions such as which fonts am I using, etc...

Here is the picture you've been waiting for
[[img]http://ompldr.org/tZXBoZg[/img]](http://ompldr.org/vZXBoZg)

---

### Post by 42dorian on 2012-07-09
At the insistence of VinDSL himself, I have been told you copied a chunk of the HowTo I wrote and put it here without permission/credit.

My personal opinion is that I'm glad my HowTo helped you get going.  But, taking 6 pages to break down how each section works goes against what I was trying to do.  The idea was that you read the entire HowTo, from top of the first post to the bottom of the first post, and it will impart all of the information you need to know in order to fix it yourself.  It contains no programming knowledge, you need no programming knowledge going into it, and it is not written to teach you to program.  All you need to do is know how to read and follow instructions.  It may be long, but it's complete.  As long as you read the whole thing, and don't skip over anything, every problem in this thread gets solved.  This includes Weather, because I've tried VinDSL's script, and I've tried the TBG alternatives.  I find VinDSL's script harder to customise than using TBG's method.  I re-directed everyone to the easier to personalise script, for their own benefit.  If you're using the Google Weather API one, you're limited to just what it spits out.  And that limits your creativity.

As a Conky person myself, I've had experience helping new people get going for quite a while now.  I wrote the HowTo with this in mind.  Quite frankly, once you get VinDSL's conky running, that isn't the end of Conky.  There is a lot more you can do with it, and narrowing your view of Conky will not be helpful to you in the future.  Once your own creativity takes over, you'll need to know how to take chunks out, and put new chunks in.  You'll need to know what else Conky can do, outside of just the handfull of things that VinDSL chose to include in his own setup.  He is awesome with design, but he isn't the be-all and end-all for what YOUR Conky can be.  This is what I had in mind when writing that HowTo to help people get started.

I say all this so that no one gets the wrong idea about this situation.  In fact, I could probably have just gone on with my day, had VinDSL not messaged me with it.  He actually felt kind of strongly that I didn't "Get Credit" for the HowTo.  His feeling on this, and his feeling alone, is the reason I mention it.  The rest is just a clarification.

---

### Post by GreatDanton on 2012-07-09
Like I mentioned in PM's, my intentions was not to steal the instructions from you, but only to make it simple. However now I know that I was wrong. Everybody who would like to have conky should do something in this way -example: reading your tutorial. If everybody will read the whole tutorial, there will be less confusion, and less questions.

Once again, I would like to thank you for this tutorial, and also I would like to thank you that you mentioned this situation. Now I understand much better the whole situation and why people should read everything.

Kind Regards

Great Danton

---

### Post by 42dorian on 2012-07-09
Yeah... I never had a problem with anything here.  This is a situation that VinDSL brought to my attention.  He mentioned that HE thought I should get credit.  He's a friend of mine here on the forums, but I still have trouble knowing when something like this upsets him or not.  I, personally, don't mind or care about credit.  But, playing it safe, I had to mention it for VinDSL's sanity (if you can call it that...) about this.

The rest?  Yes, even Quackers, can go into the HowTo and learn for themselves.  You just need to read and follow along.  No prior knowledge or skills are required.  And, when you leave again, you will not be different than you are.  Just, addicted to Conky, and equipped with the tools required to feed that addiction.  As well as pointed to a community that will, also, feed your addiction.

If there is something truly missing, or needs clarification in the HowTo?  Just let me know.  PM or in the HowTo thread.  The Big Conky Thread is fine too.  I do understand multiple broken dialects of English.  Just because I respond in proper English, doesn't mean you should feel intimidated by not knowing it yourself.  I do understand you just fine.

---

### Post by ihatethisflavorsomuch on 2012-08-24
Okay so I've been reading nonstop about this conky config for two weeks and I'm literally going bonkers over this damn conky config...when I type conky in the terminal this is what I get:


Conky: /home/wayne/.conkyrc: 104: no such configuration: 'imlib_cache_size'
Conky: llua_load: /home/wayne/.conky/draw_bg.lua:71: module 'cairo' not found:
	no field package.preload['cairo']
	no file './cairo.lua'
	no file '/usr/local/share/lua/5.1/cairo.lua'
	no file '/usr/local/share/lua/5.1/cairo/init.lua'
	no file '/usr/local/lib/lua/5.1/cairo.lua'
	no file '/usr/local/lib/lua/5.1/cairo/init.lua'
	no file '/usr/share/lua/5.1/cairo.lua'
	no file '/usr/share/lua/5.1/cairo/init.lua'
	no file '/usr/local/lib/conky/libcairo.so'
	no file './cairo.so'
	no file '/usr/local/lib/lua/5.1/cairo.so'
	no file '/usr/lib/i386-linux-gnu/lua/5.1/cairo.so'
	no file '/usr/lib/lua/5.1/cairo.so'
	no file '/usr/local/lib/lua/5.1/loadall.so'
Conky: llua_load: /home/wayne/.conky/bargraph_small.lua:158: unexpected symbol near 'if'
Conky: forked to background, pid is 18932

Conky: desktop window (1a00095) is subwindow of root window (b2)
Conky: window type - normal
Conky: drawing to created window (0x1200002)
Conky: drawing to double buffer
Conky: llua_do_call: function conky_draw_bg execution failed: attempt to call a nil value
Conky: llua_do_call: function conky_main_bars execution failed: attempt to call a nil value

(repeated for as long as conky remains open.) conky still works for the most part but it just has been urking me that everyone else has been able to get this working besides myself. The last time I had a conky problem I quit using it for 3 years.

Does anyone have any idea on how I can fix this, so I can stop smashing my head against the wall and ripping my hair out. I don't even have any more keyboards to snap in half over my knee. HELP! PLEASE!

---

