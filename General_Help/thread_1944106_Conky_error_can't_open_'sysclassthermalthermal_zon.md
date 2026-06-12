---
title: "Conky error: can't open '/sys/class/thermal/thermal_zone0/temp':"
date: 2012-03-20
forum: General Help
---

### Post by MichaelGld on 2012-03-20
I get this message every time I run Conky from the terminal. What's odd is I can't find any reference to this file/folder in my .conkyrc.  But it is true that there is no such file or folder on my system. 

My .conkyrc
```

##################################
##michael | rev. 11-06-01 00:27 ##
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
## The number of times Conky will update before quitting.
## Zero makes Conky run forever.
#
total_run_times 0

####
## Create own window instead of using desktop?
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
gap_x 6      ## Left / Right
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
color0 White        #FFFFFF
color1 Ivory        #FFFFF0
color2 Ivory2        #EEEEE0
color3 Ivory3        #CDCDC1
color4 Tan1        #FFA54F
color5 Tan2        #EE9A49
color6 Gray        #7E7E7E
color7 AntiqueWhite4    #8B8378
color8 DimGray        #696969
color9 Black        #000000

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
maximum_width 360
temperature_unit fahrenheit

TEXT
##################################
##             LOGO             ##
##################################
${voffset -33}${font OpenLogos:size=103}${color2}v${font}${voffset -76}${goto 178}${font UbuntuTitleBold:size=19.6}${color4}${offset 1}1${offset 5}1${offset 2}.0${offset 2}4${font}
##################################
##            SYSTEM            ##
##################################
${voffset 20}${font DroidSans:bold:size=8.25}${color4}SYSTEM${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font OpenLogos:size=10}${color2}u${voffset -4}${font DroidSans:size=8.65}${color3}${offset 5}${pre_exec lsb_release -sd || cat /etc/*release}${font}
${voffset 1}${offset -2}${font OpenLogos:size=12}${color2}Z${voffset -4}${font DroidSans:size=8.65}${color3}${offset 4}${sysname}${offset 5}${kernel}${alignr}${font DroidSans:size=8.45}${machine}${font}
${voffset 2}${font StyleBats:size=10}${color2}A${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}AMD${offset 3}Sempron${offset 3}140${offset 3}Edition${alignr}${font DroidSans:size=8.3}${freq_g cpu0}${offset 1}GHz${font}
${voffset 2}${font StyleBats:size=10}${color2}q${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}System${offset 3}Uptime${alignr}${font DroidSans:size=8.4}${uptime_short}${font}
CPU TEMP: ${acpitemp}°F
Updates Available: ${execi 1200 aptitude search "~U" | wc -l | tail}${font}

#################################
##          PROCESSORS          ##
##################################
#${voffset 6}${font DroidSans:bold:size=8}${color4}PROCESSORS${offset 8}${color8}${voffset -2}${hr 2}${font}
#${voffset 4}${font StyleBats:size=9.9}${color2}k${voffset -2}${font DroidSansFallback:size=8.39}${color3}${offset 2}CPU1${offset 5}${font #DroidSans:size=8.3}${cpu cpu1}%${font}
#${voffset 2}${font StyleBats:size=9.9}${color2}k${voffset -2}${font DroidSansFallback:size=8.39}${color3}${offset 2}CPU2${offset 5}${font #DroidSans:size=8.3}${cpu cpu2}%${font}

##################################
##            MEMORY            ##
##################################
${voffset 6}${font DroidSans:bold:size=8}${color4}MEMORY${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=10}${color2}l${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 3}RAM${goto 97}${font DroidSans:size=8.3}${mem}${goto 133}/${offset 5}${memmax}${alignr}${memperc}%${font}
##################################
##             HDD              ##
##################################

${voffset 16}${font DroidSans:bold:size=8}${color4}HDD${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 5}${font StyleBats:size=9.9}${color2}x${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}ROOT${goto 95}${font DroidSans:size=8.3}${fs_used /}${goto 133}/${offset 5}${fs_size /}${alignr}${fs_free_perc /}%${font}
${voffset 15}${font StyleBats:size=9.9}${color2}x${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}HOME${goto 95}${font DroidSans:size=8.3}${fs_used /home}${goto 133}/${offset 5}${fs_size /home}${alignr}${fs_free_perc /home}%${font}
${voffset 15}${font StyleBats:size=9.9}${color2}4${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}SWAP${goto 95}${font DroidSans:size=8.3}${swap}${goto 133}/${offset 5}${swapmax}${alignr}${swapperc}%
${font}

##################################
##         TOP PROCESSES        ##
##################################
${voffset 16}${font DroidSans:bold:size=8}${color4}TOP PROCESSES${offset 8}${color8}${voffset -2}${hr 2}${font}
#${voffset 18}${font DroidSans:bold:size=8}${color4}TOP PROCESSES${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 1}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 1}${alignr}${top_mem mem 1}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 2}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 2}${alignr}${top_mem mem 2}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 3}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 3}${alignr}${top_mem mem 3}%${font}
${voffset 2}${if_running rhythmbox}${voffset -16}${else}${if_running banshee}${voffset -16}${else}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 4}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 4}${alignr}${top_mem mem 4} %${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 5}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 5}${alignr}${top_mem mem 5}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 6}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 6}${alignr}${top_mem mem 6}%${endif}${endif}${font}
##################################
##           NETWORK            ##
##################################
${voffset 6}${font DroidSans:bold:size=8}${color4}NETWORK${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font PizzaDudeBullets:size=9.5}${color6}a${font DroidSans:size=8.5}${color3}${offset 5}Private${offset 3}IP${alignr}${font DroidSans:size=8.3}${addr eth0}${font}
${voffset 0}${font PizzaDudeBullets:size=9.5}${color6}a${font DroidSans:size=8.5}${color3}${offset 5}Public${offset 7}IP${alignr}  ${font DroidSans:size=8.3}${execi 1800 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}${font}
${voffset 4}${font PizzaDudeBullets:size=9.5}${color6}T${font DroidSans:size=8.5}${color3}${offset 5}Down${alignr}${font DroidSans:size=8.3}${downspeed eth0}${font}
${voffset 0}${font PizzaDudeBullets:size=9.5}${color6}N${font DroidSans:size=8.5}${color3}${offset 5}Up${alignr}${font DroidSans:size=8.3}${upspeed eth0}${font}
${voffset 4}${font PizzaDudeBullets:size=9.5}${color6}T${font DroidSans:size=8.5}${color3}${offset 5}Downloaded${alignr}${font DroidSans:size=8.3}${totaldown eth0}${font}
${voffset 0}${font PizzaDudeBullets:size=9.5}${color6}N${font DroidSans:size=8.5}${color3}${offset 5}Uploaded${alignr}${font DroidSans:size=8.3}${totalup eth0}${font}
# changed all instances of eth0 to eth2 based on results from ifconfig.  03022012.
##################################
##      Graphics  ##
##################################

# ${voffset 6}${font DroidSans:bold:size=8}${color4}GRAPHICS ${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 6}${font DroidSans:bold:size=8}${color4}GRAPHICS ${offset 8}${color8}${voffset -2}${hr 2}
# ${font Terminus:style=bold:size=11}GRAPHICS $hr${font}
#${font DroidSans:size=8.5}
${font}GPU TEMP: ${nvidia temp }°F${font Terminus:size=7}${alignr}Threshold temp ${nvidia threshold}°F
#${font DroidSans:size=8.5}
${execp ~/conkygraphics.sh}${font}${color orange}
##################################
##      WEATHER (Imperial)      ##
##################################
#${voffset 6}${font DroidSans:bold:size=8}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
#${voffset 2}${goto 38}${font Weather:size=43.5}${color2}y${font}
#${voffset -50}${font RadioSpace:size=32}${color3}${alignc}${execi 1800 conkyForecast -d HT -i}${font}
#${voffset -33}${goto 199}${font DroidSansFallback:bold:size=7.55}${color6}H:${offset 1}${execpi 1800 conkyForecast -d HT -s 0 -ui | sed -e 's/N\/A'/'\$\{color7}TBA\$\{color6}/g'}${voffset 15}${goto 200}L:${offset 2}${execi 1800 conkyForecast -d LT -s 0 -ui}${font}
#${voffset -40}${font KRARound:size=36}${color7}${goto 185}I${font}
#${voffset 4}${font Ubuntu:size=23}${color4}${alignc}${execpi 1800 conkyForecast -d CT}${font}
#${voffset 12}${goto 20}${font ConkyWindNESW:size=41}${color3}${execi 1800 conkyForecast -d BS}${font}${voffset -40}${goto 98}${font #ConkyWeather:size=45}${execi 1800 conkyForecast -d WF}${font}${voffset -39}${goto 188}${font MoonPhases:size=32}${execi 1800 conkyForecast -#d MF}${font}
#${voffset 6}${goto 28}${font DroidSansFallback:bold:size=8.45}${color4}${execpi 1800 conkyForecast -d WS -i | sed -e 's/calm'/'\$\{offset 2}Calm/g' -e 's/mph'/'\$\{offset 3}mph/g'}${goto 88}Feels like ${execi 1800 conkyForecast -d LT -ui}${execpi 1800 conkyForecast -d MP| sed -e #'s/First.*'/'\$\{goto 182}First Qtr/g' -e 's/Last.*'/'\$\{goto 184}Last Qtr/g' -e 's/New.*'/'\$\{goto 195}New/g' -e 's/Full.*'/'\$\{goto 195}#Full/g' -e 's/Waning.*'/'\$\{goto 187}Waning/g' -e 's/Waxing.*'/'\$\{goto 187}Waxing/g'}${font}
#${voffset 9}${goto 36}${font DroidSansMono:bold:size=8.35}${color3}${execi 1800 conkyForecast -d DW -s 1 -w}${goto 89}${execi 1800 #conkyForecast -d DW -s 2 -w}${goto 143}${execi 1800 conkyForecast -d DW -s 3 -w}${goto 197}${execi 1800 conkyForecast -d DW -s 4 -w}${font}
#${voffset 2}${goto 25}${font ConkyWeather:size=32}${color3}${execi 1800 conkyForecast -d WF -s 1 -e 4 -S 1}${font}
#${voffset 0}${goto 25}${font DroidSans:bold:size=8.5}${color4}${execi 1800 conkyForecast -d HT -s 1 -ui}${offset 2}/${offset 2}${execi 1800 #conkyForecast -d LT -s 1 -ui}${goto 79}${execi 1800 conkyForecast -d HT -s 2 -ui}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s #2 -ui}${goto 133}${execi 1800 conkyForecast -d HT -s 3 -ui}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 3 -ui}${goto 187}${execi 1800 conkyForecast -d HT -s 4 -ui}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 4 -ui}${font}

##################################
##     WEATHER (Imperial)       ##
##################################
# ${voffset 4}${font DroidSans:bold:size=8.25}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
# ${voffset -55}${font RadioSpace:size=34}${color3}${execi 1800 /home/michael/.conky/weather/weather.sh #"Scottsdale,AZ" ctbi}${font}${voffset -28}${goto 33}${font Weather:size=42}${color3}y${font}
# ${voffset -38}${font Ubuntu:size=8.63}${color5}${execi 1800 /home/michael/.conky/weather/weather.sh #"Scottsdale,AZ" ctti}${font}
# ${voffset -39}${font KRARound:size=36}${color3}${goto 195}I${font}
# ${voffset 6}${font Ubuntu:size=23}${color5}${alignc -2}${execi 1800 /home/michael/.conky/weather/weather.sh #"Scottsdale,AZ" ccb}${font}
# ${voffset 8}${font DroidSansFallback:size=8.63}${color3}${execi 1800 /home/michael/.conky/weather/weather.sh #"Scottsdale,AZ"}${font}
# ${voffset -57}${font ConkyWeather:size=48}${color6}${alignc -55}${execi 1800 /home/michael/.conky/weather/#weather.sh "Scottsdale,AZ" cp}${font}
# ${voffset 6}${font DroidSansMono:bold:size=8.62}${color4}${offset 40}${execi 1800 /home/michael/.conky/#weather/weather.sh "Scottsdale,AZ" dl}${font}
#${voffset 0}${font ConkyWeather:size=37.9}${color3}${offset 26}${execi 1800 /home/michael/.conky/weather/#weather.sh "Scottsdale,AZ" fcp}${font}
# ${voffset 0}${font DroidSansFallback:bold:size=8.62}${color4}${offset 28}${execi 1800 /home/michael/.conky/#weather/weather.sh "Scottsdale,AZ" fcti}${font}


#${color red}WEATHER ${font}${hr 2}${execi 600 bash /home/michael/accuweather_conky_USA/accuw_USA_script}
${voffset 4}${font DroidSans:bold:size=8.25}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
${font conkyweather:size=40}${execi 600  sed -n '6p' ~/accuweather_conky_USA/images}${font}${goto 75}${voffset -40}${execpi 600 sed -n '1p' /home/michael/accuweather_conky_USA/days}:
${goto 75}${execpi 600 sed -n '2p' /home/michael/accuweather_conky_USA/messages|fold -w36}
${goto 75}High: ${execpi 600 sed -n '1p' /home/michael/accuweather_conky_USA/temperatures}°F  Low: ${execpi 600 sed -n '2p' /home/michael/accuweather_conky_USA/temperatures}°F

${font conkyweather:size=40}${execi 600  sed -n '7p' ~/accuweather_conky_USA/images}${font}${goto 75}${voffset -40}${execpi 600 sed -n '2p' /home/michael/accuweather_conky_USA/days}:
${goto 75}${execpi 600 sed -n '5p' /home/michael/accuweather_conky_USA/messages|fold -w36}
${goto 75}High: ${execpi 600 sed -n '3p' /home/michael/accuweather_conky_USA/temperatures}°F  Low: ${execpi 600 sed -n '4p' /home/michael/accuweather_conky_USA/temperatures}°F

${font conkyweather:size=40}${execi 600  sed -n '8p' ~/accuweather_conky_USA/images}${font}${goto 75}${voffset -40}${execpi 600 sed -n '3p' /home/michael/accuweather_conky_USA/days}:
${goto 75}${execpi 600 sed -n '8p' /home/michael/accuweather_conky_USA/messages|fold -w36}
${goto 75}High: ${execpi 600 sed -n '5p' /home/michael/accuweather_conky_USA/temperatures}°F  Low: ${execpi 600 sed -n '6p' /home/michael/accuweather_conky_USA/temperatures}°F

${font conkyweather:size=40}${execi 600  sed -n '9p' ~/accuweather_conky_USA/images}${font}${goto 75}${voffset -40}${execpi 600 sed -n '4p' /home/michael/accuweather_conky_USA/days}:
${goto 75}${execpi 600 sed -n '11p' /home/michael/accuweather_conky_USA/messages|fold -w36}
${goto 75}High: ${execpi 600 sed -n '7p' /home/michael/accuweather_conky_USA/temperatures}°F  Low: ${execpi 600 sed -n '8p' /home/michael/accuweather_conky_USA/temperatures}°F

${font conkyweather:size=40}${execi 600  sed -n '10p' ~/accuweather_conky_USA/images}${font}${goto 75}${voffset -40}${execpi 600 sed -n '5p' /home/michael/accuweather_conky_USA/days}:
${goto 75}${execpi 600 sed -n '14p' /home/michael/accuweather_conky_USA/messages|fold -w36}
${goto 75}High: ${execpi 600 sed -n '9p' /home/michael/accuweather_conky_USA/temperatures}°F  Low: ${execpi 600 sed -n '10p' /home/michael/accuweather_conky_USA/temperatures}°F


# 12/13/11--Changed fold -w25 to -w26. This had the desired effet of extending the second line of text in the weather section # so the text is not truncated to exclude some letters of the forecast.

# 03/07/12--Changed fold -w26 to -w36. This had the desired effet of extending the second line of text in the weather section # so the text is not truncated to exclude some letters of the forecast.

##################################
##      WEATHER (Metric)        ##
##################################
# ${voffset 6}${font DroidSans:bold:size=8}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
# ${voffset 2}${goto 38}${font Weather:size=43.5}${color2}y${font}
# ${voffset -50}${font RadioSpace:size=32}${color3}${alignc}${execi 1800 conkyForecast -d HT}${font}
# ${voffset -33}${goto 199}${font DroidSansFallback:bold:size=7.55}${color6}H:${offset 1}${execpi 1800 conkyForecast -d HT -s 0 -u | sed -e #'s/N\/A'/'\$\{color7}TBA\$\{color6}/g'}${voffset 15}${goto 200}L:${offset 2}${execi 1800 conkyForecast -d LT -s 0 -u}${font}
# ${voffset -40}${font KRARound:size=36}${color7}${goto 185}I${font}
# ${voffset 4}${font Ubuntu:size=23}${color4}${alignc}${execpi 1800 conkyForecast -d CT}${font}
# ${voffset 12}${goto 20}${font ConkyWindNESW:size=41}${color3}${execi 1800 conkyForecast -d BS}${font}${voffset -40}${goto 98}${font #ConkyWeather:size=45}${execi 1800 conkyForecast -d WF}${font}${voffset -39}${goto 188}${font MoonPhases:size=32}${execi 1800 conkyForecast -#d MF}${font}
# ${voffset 6}${goto 30}${font DroidSansFallback:bold:size=8.45}${color4}${execpi 1800 conkyForecast -d WS | sed -e 's/calm'/'\$\{offset 2}#Calm/g' -e 's/kph'/'\$\{offset 3}kph/g'}${goto 88}Feels like ${execi 1800 conkyForecast -d LT -u}${execpi 1800 conkyForecast -d MP | sed -e #'s/First.*'/'\$\{goto 182}First Qtr/g' -e 's/Last.*'/'\$\{goto 184}Last Qtr/g' -e 's/New.*'/'\$\{goto 195}New/g' -e 's/Full.*'/'\$\{goto 195}#Full/g' -e 's/Waning.*'/'\$\{goto 187}Waning/g' -e 's/Waxing.*'/'\$\{goto 187}Waxing/g'}${font}
# ${voffset 9}${goto 36}${font DroidSansMono:bold:size=8.35}${color3}${execi 1800 conkyForecast -d DW -s 1 -w}${goto 89}${execi 1800 #conkyForecast -d DW -s 2 -w}${goto 143}${execi 1800 conkyForecast -d DW -s 3 -w}${goto 197}${execi 1800 conkyForecast -d DW -s 4 -w}${font}
# ${voffset 2}${goto 25}${font ConkyWeather:size=32}${color3}${execi 1800 conkyForecast -d WF -s 1 -e 4 -S 1}${font}
# ${voffset 0}${goto 25}${font DroidSans:bold:size=8.5}${color4}${execi 1800 conkyForecast -d HT -s 1 -u}${offset 2}/${offset 2}${execi 1800 #conkyForecast -d LT -s 1 -u}${goto 79}${execi 1800 conkyForecast -d HT -s 2 -u}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 2 -#u}${goto 133}${execi 1800 conkyForecast -d HT -s 3 -u}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 3 -u}${goto 187}${execi #1800 #conkyForecast -d HT -s 4 -u}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 4 -u}${font}
##################################
##             TIME             ##
##################################
${voffset 6}${font DroidSans:bold:size=8}${color4}TIME${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset -4}${font RadioSpace:size=32}${color3}${if_match ${time %l}<=9}${alignc 7}${time %l:%M%p}${else}${if_match ${time %l}>=10}${alignc -1}${time %l:%M%p}${endif}${endif}${font}
${voffset 0}${font DroidSansFallback:bold:size=6.85}${color4}${alignc 2}Sunrise${offset 1}${execi 1800 conkyForecast -d SR}${color3}${offset 2}|${offset 2}${color4}Sunset${offset 1}${execi 1800 conkyForecast -d SS}${font}
##################################
##           CALENDAR           ##
##################################
#${voffset 4}${font DroidSans:bold:size=8}${color4}DATE${offset 8}${color8}${voffset -2}${hr 2}${font}
#${voffset 16}${font DroidSansMono:size=7.55}${color3}${alignc 60}${time %A}${font}
#${voffset -4}${if_match ${time %e}<=9}${font DroidSansFallback:bold:size=18}${color5}${alignc 65}${time %e}${font}${else}${if_match ${time %e}>=10}${font DroidSansFallback:bold:size=18}${color5}${alignc 60}${time %e}   ${endif}${endif}${font}
${voffset 0}${font DroidSansMono:size=7.55}${color3}${alignc 60}${time %B}${font}
${voffset 0}${font DroidSansMono:size=7.6}${color3}${alignc 60}${time %Y}${font}
####
## Uncomment for Conky 1.8.0
${voffset -75}${font DroidSansMono:size=7.55}${color3}${execpi 60michael_Cal_8=`date +%-d`; cal -h | sed -e '1d' -e s/^/"\$\{offset 100"\}/ -e 's/\<'"$michael_Cal_8"'\>/${color4}&${color3}/'}${font}
####
## Uncomment for Conky 1.8.1
#  ${voffset -75}${offset 100}${font DroidSansMono:size=7.55}${color3}${execpi 60michael_Cal_8=`date +%-d`; cal -h | sed -e '1d' -e 's/\<'"$michael_Cal_8"'\>/${color4}&${color3}/'}${font}
${voffset -99}${font CutOutsFor3DFX:size=67}${color8}${alignc 99}2${font}
##################################
##          RHYTHMBOX           ##
##################################
${if_running rhythmbox}${voffset 21}${font DroidSans:bold:size=7.75}${color4}RHYTHMBOX${offset 8}${color8}${voffset -2}${hr 2}${endif}${font}
${if_running rhythmbox}${voffset 10}${font DroidSans:size=8.25}${color3}${if_match "${execpi 2 expr length "`/usr/bin/rhythmbox-client --print-playing-format %tt | head -n 1`"}" >= "48"}${alignr}${scroll 38 4* ${execi 2 rhythmbox-client --print-playing-format %tt --no-start}}${font}${else}${alignc}${execi 2 rhythmbox-client --print-playing-format %tt --no-start}${endif}${endif}${font}
##################################
##    BANSHEE (Experimental)    ##
##################################
${if_running banshee}${voffset -5}${font DroidSans:bold:size=7.75}${color4}BANSHEE${offset 8}${color8}${voffset -2}${hr 2}${voffset 31}${endif}${font}
${if_running banshee}${voffset -28}${font DroidSans:size=8.25}${color3}${if_match "${execpi 16 expr length "`/usr/bin/banshee --query-title --no-present | cut -f1- -d " "`"}" >= "48"}${alignr}${scroll 38 4* ${execi 2 banshee --query-title --no-present | cut -f2- -d " "}}${font}${else}${alignc}${execi 2 banshee --query-title --no-present | cut -f2- -d " "}${endif}${endif}${font}
```Any help would be appreciated.

---

### Post by vladkras on 2012-06-19
same problem
my cut of .conkyrc from official project page
```
background		no
use_xft			yes
xftfont			Courier:size=12
double_buffer		yes
update_interval		2
alignment		top_left
gap_x			10
gap_y			10
no_buffers		yes
minimum_size 		365x500
pad_percents		3

TEXT
${color #FF0000}$nodename - $sysname $kernel
${color #0000FF}Uptime: $uptime
RAM: $memperc% ${membar 8}
Swap:$swapperc% ${swapbar 8}
CPU: $cpu% ${cpubar 8}
CPU Temp: ${acpitemp}C
${color #FFFF00}/       ${fs_used /}/${fs_size /}${alignr}${fs_used_perc /}%
${fs_bar 8 /}
/home   ${fs_used /home}/${fs_size /home}${alignr}${fs_used_perc /home}%
${fs_bar 8 /home}
${color #00FF00}Down: ${downspeedf eth0}k/s ${alignr}${totaldown eth0} total
${downspeedgraph eth0}
${color #00FF00}Up: ${upspeedf eth0}k/s ${alignr}${totalup eth0} total
${upspeedgraph eth0}
```

conky window doesn't even appear when I create it in home folder

---

### Post by dcottingham on 2012-06-19
A few questions.
1. Do you have /sys?
2. Do you have /sys/class/thermal?
3. What is in your /sys/class/thermal?

---

### Post by MichaelGld on 2012-06-19
> **dcottingham said:**
> A few questions.
1. Do you have /sys?
2. Do you have /sys/class/thermal?
3. What is in your /sys/class/thermal?

I now have a folder called /sys/class/thermal. The folllwing files are located there:

```
michael@michael-desktop:/sys/class/thermal$ ls -l
total 0
lrwxrwxrwx 1 root root 0 2012-06-19 02:57 cooling_device0 -> ../../devices/virtual/thermal/cooling_device0
lrwxrwxrwx 1 root root 0 2012-06-19 02:57 cooling_device1 -> ../../devices/virtual/thermal/cooling_device1
lrwxrwxrwx 1 root root 0 2012-06-19 02:57 cooling_device2 -> ../../devices/virtual/thermal/cooling_device2
lrwxrwxrwx 1 root root 0 2012-06-19 02:57 cooling_device3 -> ../../devices/virtual/thermal/cooling_device3
michael@michael-desktop:/sys/class/thermal$ 
```

---

### Post by dcottingham on 2012-06-21
My best guess is that your hardware has no temperature sensor -- or at least none recognized by any driver you have installed.

I would run "sudo sensors-detect". If you don't have sensors-detect, you can get it by "sudo apt-get install lm-sensors". sensors-detect checks for hardware sensors, and if it finds any it tells you what drivers you should install to get them working.

---

