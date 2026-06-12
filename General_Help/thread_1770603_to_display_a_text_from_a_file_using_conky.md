---
title: "to display a text from a file using conky"
date: 2011-05-29
forum: General Help
---

### Post by anoopm101 on 2011-05-29
i have the following text in a file located in /home/anoopm101/.task

[description:"this is the text" entry:"1306682734" status:"pending" uuid:"25c54e1b-824f-52bc-4933-dfe7cda34bc7"]

i have to display on my desktop "this is the text" using conky.

please help me with the command to do it.

---

### Post by blueridgedog on 2011-05-29
[http://ubuntuforums.org/showthread.php?t=733959](http://ubuntuforums.org/showthread.php?t=733959)

---

### Post by wildmanne39 on 2011-05-29
> **anoopm101 said:**
> i have the following text in a file located in /home/anoopm101/.task

[description:"this is the text" entry:"1306682734" status:"pending" uuid:"25c54e1b-824f-52bc-4933-dfe7cda34bc7"]

i have to display on my desktop "this is the text" using conky.

please help me with the command to do it.Hi, I will show you an example of my conkyrc file but I am not an expert.

 /home/larry/.conkyrc
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
gap_y 31

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
${voffset -33}${font OpenLogos:size=103}${color0}v${font}${voffset -76}${goto 178}${font UbuntuTitleBold:size=19.6}${color4}${offset 1}1${offset 5}1${offset 2}.04${font}
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
##      WEATHER (Imperial)      ##
##################################
${voffset 6}${font DroidSans:bold:size=8}${color4}WEATHER${offset 8}${color0}${voffset -2}${hr 2}${font}
${voffset 0}${goto 59}${font Weather:size=38}${color2}y${font}${voffset -33}${offset 14}${font RadioSpace:size=32}${color3}${execi 1800 conkyForecast -d HT -i}${font}
${voffset 0}${font Ubuntu:size=24}${color4}${alignc}${execi 1800 conkyForecast -d CT}${font}
${voffset 10}${goto 20}${font ConkyWindNESW:size=41}${color3}${execi 1800 conkyForecast -d BS}${font}${voffset -40}${goto 98}${font ConkyWeather:size=45}${execi 1800 conkyForecast -d WF}${font}${voffset -39}${goto 188}${font MoonPhases:size=32}${execi 1800 conkyForecast -d MF}${font}
${voffset 6}${goto 28}${font DroidSansFallback:bold:size=8.45}${color4}${execpi 1800 conkyForecast -d WS -i| sed -e 's/calm'/'\$\{offset 2}Calm/g' -e 's/mph'/'\$\{offset 3}mph/g'}${goto 88}Feels like ${execi 1800 conkyForecast -d LT -ui}${execpi 1800 conkyForecast -d MP| sed -e 's/First.*'/'\$\{goto 182}First Qtr/g' -e 's/Last.*'/'\$\{goto 184}Last Qtr/g' -e 's/New.*'/'\$\{goto 195}New/g' -e 's/Full.*'/'\$\{goto 195}Full/g' -e 's/Waning.*'/'\$\{goto 187}Waning/g' -e 's/Waxing.*'/'\$\{goto 187}Waxing/g'}${font}
${voffset 9}${goto 36}${font DroidSansMono:bold:size=8.35}${color3}${execi 1800 conkyForecast -d DW -s 1 -w}${goto 89}${execi 1800 conkyForecast -d DW -s 2 -w}${goto 143}${execi 1800 conkyForecast -d DW -s 3 -w}${goto 197}${execi 1800 conkyForecast -d DW -s 4 -w}${font}
${voffset 2}${goto 25}${font ConkyWeather:size=32}${color3}${execi 1800 conkyForecast -d WF -s 1 -e 4 -S 1}${font}
${voffset 0}${goto 25}${font DroidSans:bold:size=8.5}${color4}${execi 1800 conkyForecast -d HT -s 1 -ui}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 1 -ui}${goto 79}${execi 1800 conkyForecast -d HT -s 2 -ui}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 2 -ui}${goto 133}${execi 1800 conkyForecast -d HT -s 3 -ui}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 3 -ui}${goto 187}${execi 1800 conkyForecast -d HT -s 4 -ui}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 4 -ui}${font}
##################################
##      WEATHER (Metric)        ##
##################################
# ${voffset 6}${font DroidSans:bold:size=8}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
# ${voffset 0}${goto 59}${font Weather:size=38}${color2}y${font}${voffset -33}${offset 14}${font RadioSpace:size=32}${color3}${execi 1800 conkyForecast -d HT}${font}
# ${voffset 0}${font Ubuntu:size=24}${color4}${alignc}${execi 1800 conkyForecast -d CT}${font}
# ${voffset 10}${goto 20}${font ConkyWindNESW:size=41}${color3}${execi 1800 conkyForecast -d BS}${font}${voffset -40}${goto 98}${font ConkyWeather:size=45}${execi 1800 conkyForecast -d WF}${font}${voffset -39}${goto 188}${font MoonPhases:size=32}${execi 1800 conkyForecast -d MF}${font}
# ${voffset 6}${goto 30}${font DroidSansFallback:bold:size=8.45}${color4}${execpi 1800 conkyForecast -d WS | sed -e 's/calm'/'\$\{offset 2}Calm/g' -e 's/kph'/'\$\{offset 3}kph/g'}${goto 88}Feels like ${execi 1800 conkyForecast -d LT -u}${execpi 1800 conkyForecast -d MP| sed -e 's/First.*'/'\$\{goto 182}First Qtr/g' -e 's/Last.*'/'\$\{goto 184}Last Qtr/g' -e 's/New.*'/'\$\{goto 195}New/g' -e 's/Full.*'/'\$\{goto 195}Full/g' -e 's/Waning.*'/'\$\{goto 187}Waning/g' -e 's/Waxing.*'/'\$\{goto 187}Waxing/g'}${font}
# ${voffset 9}${goto 36}${font DroidSansMono:bold:size=8.35}${color3}${execi 1800 conkyForecast -d DW -s 1 -w}${goto 89}${execi 1800 conkyForecast -d DW -s 2 -w}${goto 143}${execi 1800 conkyForecast -d DW -s 3 -w}${goto 197}${execi 1800 conkyForecast -d DW -s 4 -w}${font}
# ${voffset 2}${goto 25}${font ConkyWeather:size=32}${color3}${execi 1800 conkyForecast -d WF -s 1 -e 4 -S 1}${font}
# ${voffset 0}${goto 25}${font DroidSans:bold:size=8.5}${color4}${execi 1800 conkyForecast -d HT -s 1 -u}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 1 -u}${goto 79}${execi 1800 conkyForecast -d HT -s 2 -u}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 2 -u}${goto 133}${execi 1800 conkyForecast -d HT -s 3 -u}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 3 -u}${goto 187}${execi 1800 conkyForecast -d HT -s 4 -u}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 4 -u}${font}
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
${voffset 16}${font DroidSansMono:size=7.55}${color2}${alignc 60}${time %A}${font}
${voffset -4}${if_match ${time %e}<=9}${font DroidSansFallback:bold:size=18}${color4}${alignc 65}${time %e}${font}${else}${if_match ${time %e}>=10}${font DroidSansFallback:bold:size=18}${color4}${alignc 60}${time %e}${endif}${endif}${font}
${voffset 0}${font DroidSansMono:size=7.55}${color2}${alignc 60}${time %B}${font}
${voffset 0}${font DroidSansMono:size=7.6}${color2}${alignc 60}${time %Y}${font}
####
## Uncomment for Conky 1.8.0
${voffset -75}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_8=`date +%-d`; cal -h | sed -e '1d' -e s/^/"\$\{offset 110"\}/ -e 's/\<'"$VinDSL_Cal_8"'\>/${color4}&${color3}/'}${font}
####
## Uncomment for Conky 1.8.1
#  ${voffset -75}${offset 100}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_8=`date +%-d`; cal -h | sed -e '1d' -e 's/\<'"$VinDSL_Cal_8"'\>/${color4}&${color3}/'}${font}
${voffset -99}${font CutOutsFor3DFX:size=67}${color8}${alignc 99}2${font}
##################################
##          RHYTHMBOX           ##
##################################
${if_running rhythmbox}${voffset 21}${font DroidSans:bold:size=7.75}${color4}RHYTHMBOX${offset 8}${color0}${voffset -2}${hr 2}${endif}${font}
${if_running rhythmbox}${voffset 10}${font DroidSans:size=12}${color2}${if_match "${execpi 2 expr length "`/usr/bin/rhythmbox-client --print-playing-format %tt | head -n 1`"}" >= "45"}${alignr}${scroll 38 4* ${execi 2 rhythmbox-client --print-playing-format %tt --no-start}}${font}${else}${alignc}${execi 2 rhythmbox-client --print-playing-format %tt --no-start}${endif}${endif}${font}
##################################
##    BANSHEE (Experimental)    ##
##################################
${if_running banshee}${voffset -5}${font DroidSans:bold:size=7.75}${color4}BANSHEE${offset 8}${color8}${voffset -2}${hr 2}${voffset 31}${endif}${font}
${if_running banshee}${voffset -24}${font DroidSans:size=8.25}${color3}${if_match "${execpi 10 expr length "`/usr/bin/banshee --query-title --no-present | cut -f1- -d " "`"}" >= "50"}${alignr}${scroll 45 4* ${execi 10 banshee --query-title --no-present | cut -f2- -d " "}}${font}${else}${alignc}${execi 10 banshee --query-title --no-present | cut -f2- -d " "}${endif}${endif}${font}

```Now any text that is below the text line that is not commented out or in brackets except the dollar signs will show up on the screen. When you are ready I will answer more questions. You will have to create it in the home folder not root, and you will need a bash script to make it sleep while ubuntu boots. I will attache that as well. This is my bash script.

ssc.sh
```
conky -p 40 -c ~/.conkyrc &
conky -p 40 -c ~/.conkyrc1 &
conky -p 40 -c ~/.conkyrc2 &
exit
```

---

