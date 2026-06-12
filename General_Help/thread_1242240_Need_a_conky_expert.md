---
title: "Need a conky expert"
date: 2009-08-16
forum: General Help
---

### Post by ali999 on 2009-08-16
Hi

I recently got conky on my computer but am still trying to configure it properly. I got my configuration file from the internet. This is what it looks like:

```
# Conky configuration
# of cbrman.
###For a correct work, edit it and delete all the lines that start with ### below the line called TEXT. They are notes about make it work.
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont sans:size=7:bold

# Text alpha when using Xft
xftalpha 0.8

# MPD host/port
#mpd_host localhost
#mpd_port 6600
#mpd_password tinker_bell

#Print everything to console?
out_to_console no

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
#own_window_colour black

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 210 5

# Maximum width of window
maximum_width 215

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
stippled_borders 1

# border margins
border_margin 4

# border width
border_width 0

# Default colors and also border colors
default_color #cccccc
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 5
gap_y 0 # To hide from tranparent window borders.

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about? This only affects certain objects.
use_spacer none

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
max_user_text 16384

TEXT
${voffset -5}${color #f8ec1e}${font undotum:size=30:bold}${time %e}${font}
${voffset -33}${goto 65}${#f8ec1e}${font undotum:size=10}${time %A}${font}, ${voffset -7}${#f8ec1e}${font undotum:size=12}${time %B}${font} ${voffset -7}${color #f8ec1e}${font undotum:size=12:bold}${time %G}${font}
${voffset -2}${goto 65}${color #f2f2f2}${font undotum:size=12:bold}${time %H:%M:%S%z %P}${font}
${voffset 12}${font openlogos:size=20}${font}${voffset -50}
${voffset 18}${goto 22}${color #28AF63}${color #28AF63}$sysname ${color #FF6600} $kernel ${color #28AF63}Ubuntu ${color #FF6600}$machine${voffset -18}
${voffset 16}${goto 22}${color #28AF63}Uptime:${color #FF6600} $uptime ${color #28AF63}Load:${color #FF6600} $loadavg${voffset -18}
${voffset 18}${goto 22}${color #28AF63}CPU: ${color #28AF63}${cpubar 7,92} ${color #FF6600} $cpu%
${voffset -27}${goto 500}${color #FF6600}${font Openlogos:size=20}${font}
${color #28AF63}${cpugraph 15,203 FF6600 f2f2f2}
${color #28AF63}RAM: ${color #FF6600}$mem/$memmax - $memperc% ${color #28AF63}${alignr 2}${membar 7,45}
${color #28AF63}Swap: ${color #FF6600}$swap/$swapmax - $swapperc% ${color #28AF63}${alignr 2}${swapbar 7,46}
${color #28AF63}Processes: ${color #FF6600}$processes ${color #28AF63}CPU freqency: ${color #FF6600}${freq 1}MHz
${color #f8ec1e}${font OpenLogos:size=25}J${color #f8ec1e}${font 28 Days Later:size=10} WEATHER $stippled_hr${font}
${offset 4}${color whitesmoke}${execi 1680 python /home/ali/.scripts/conkyForecast.py --location=CAXX0273 --datatype=CN --refetch}
${color #28AF63}Today's Conditions:${offset 4}${color whitesmoke}${execi 1680 python /home/ali/.scripts/conkyForecast.py --location=CAXX0273 --datatype=CT}
${offset 36}${voffset -4}${color #28AF63}${font Weather:size=54}${execi 1680 python /home/ali/.scripts/conkyForecast.py --location=CAXX0273 --datatype=WF}${font}
${voffset -8}${color #28AF63}Temperature: ${color whitesmoke}${execi 1680 python /home/ali/.scripts/conkyForecast.py --location=CAXX0273 --datatype=HT} ${color #28AF63}Windspeed: ${color whitesmoke}${execi 1680 python /home/ali/.scripts/conkyForecast.py --location=CAXX0273 --datatype=WS}
${color #28AF63}Direction: ${color whitesmoke}${execi 1680 python /home/ali/.scripts/conkyForecast.py --location=CAXX0273 --datatype=WD} ${color #28AF63}Humidity: ${color whitesmoke}${execi 1680 python /home/ali/.scripts/conkyForecast.py --location=CAXX0273 --datatype=HM}
${color #28AF63}${stippled_hr 1}
${color #28AF63}Tomorrow: ${offset 4}${color #f8ec1e}${execi 1680 python /home/ali/.scripts/conkyForecast.py --location=CAXX0273 --datatype=CT --startday=1 --endday=1}
${color #28AF63}${stippled_hr 1}
${offset 20}${color #f8ec1e}${execi 1680 python /home/ali/.scripts/conkyForecast.py --location=CAXX0273 --datatype=DW --shortweekday --startday=1 --endday=3 --spaces=15}
${offset 14}${color whitesmoke}${font Weather:size=30}${execi 1680 python /home/ali/.scripts/conkyForecast.py --location=CAXX0273 --datatype=WF --startday=1 --endday=3 --spaces=9}${font}
${voffset -7}${color #28AF63}Max: ${color #FF6600}${execi 1680 python /home/ali/.scripts/conkyForecast.py --location=CAXX0273 --datatype=HT --startday=1 --endday=3 --spaces=13}
${color #28AF63}Min: ${color #FF6600}${execi 1680 python /home/ali/.scripts/conkyForecast.py --location=CAXX0273 --datatype=LT --startday=1 --endday=3 --spaces=14}
${color #28AF63}Hum: ${color #FF6600}${execi 1680 python /home/ali/.scripts/conkyForecast.py --location=CAXX0273 --datatype=HM --startday=1 --endday=3 --spaces=13}
${color #f8ec1e}${font Poky:size=20}a${color #f8ec1e}${font 28 Days Later:size=10} PROCESSES $stippled_hr ${font}
${color #28AF63}Name ::. ${goto 110}PID${goto 138}CPU%${goto 175}MEM%
${color #FF6600}${top name 1} ${goto 105}${top pid 1}${goto 138}${top cpu 1}${goto 175}${top mem 1}
${color #FF6600}${top name 2} ${goto 105}${top pid 2}${goto 138}${top cpu 2}${goto 175}${top mem 2}
${color #FF6600}${top name 3} ${goto 105}${top pid 3}${goto 138}${top cpu 3}${goto 175}${top mem 3}
${color #FF6600}${top name 4} ${goto 105}${top pid 4}${goto 138}${top cpu 3}${goto 175}${top mem 4}
${color #28AF63}Memory ::.
${color #FF6600}${top_mem name 1} ${goto 105}${top_mem pid 1}${goto 138}${top_mem cpu 1}${goto 175}${top_mem mem 1}
${color #FF6600}${top_mem name 2} ${goto 105}${top_mem pid 2}${goto 138}${top_mem cpu 2}${goto 175}${top_mem mem 2}
${color #FF6600}${top_mem name 3} ${goto 105}${top_mem pid 3}${goto 138}${top_mem cpu 3}${goto 175}${top_mem mem 3}
${color #FF6600}${top_mem name 4} ${goto 105}${top_mem pid 4}${goto 138}${top_mem cpu 4}${goto 175}${top_mem mem 4}
${color #f8ec1e}${font Poky:size=20}f${color #f8ec1e}${font 28 Days Later:size=10} HARD DRIVE INFO $stippled_hr ${font}
${color #28AF63}Root ${goto 50}${color #FF6600}${fs_used /}/${fs_size /} ${color #28AF63}${alignr 2}${fs_bar 7,60 /}
${color #28AF63}Home ${goto 50}${color #FF6600}${fs_used /home}/${fs_size /home} ${color #28AF63}${alignr 2}${fs_bar 7,60 /home}
${color #f8ec1e}${font Poky:size=20}l${color #f8ec1e}${font 28 Days Later:size=10} MUSIC $stippled_hr${font}
${color #28AF63}${alignc}CURRENT SONG INFO ::.
${if_running rhythmbox}${color #28AF63}Artist: ${color #FF6600}${goto 50}${exec rhythmbox-client --no-start --print-playing-format %ta}
${color #28AF63}Title: ${color #FF6600}${goto 50}${exec rhythmbox-client --print-playing-format %tt}
${color #28AF63}Album: ${color #FF6600}${goto 50}${exec rhythmbox-client --no-start --print-playing-format %at}
${color #28AF63}Genre: ${color #FF6600}${goto 50}${exec rhythmbox-client --no-start --print-playing-format %ag}${goto 130}${color #28AF63}Year: ${color #FF6600}${exec rhythmbox-client --no-start --print-playing-format %ay}
${color #28AF63}Position: ${color #FF6600}${exec rhythmbox-client --no-start --print-playing-format %te}${goto 130}${color #28AF63}Length: ${color #FF6600}${exec rhythmbox-client --no-start --print-playing-format %td}${color #28AF63}$else${color #f2f2f2}${alignc}${font sans:size=6:bold}No Activity${font}$endif
${color #f8ec1e}${font Poky:size=20}w${color #f8ec1e}${font 28 Days Later:size=10} NETWORKING $stippled_hr ${font}
${color #28AF63}My IP Address: ${color #FF6600}${execi 10000 curl 'http://www.whatismyip.org'}
${color #28AF63}WiFi Network: ${color #FF6600} ${wireless_essid wlan0} ${color #FF6600} ${wireless_bitrate wlan0} ${wireless_link_qual wlan0}%
${color #28AF63}${wireless_link_bar wlan0}
```

I've attached a screenshot of what it looks like. As you can see there is some cleaning up that needs to be done. I don't know what is the deal with all these letter or how I can get rid of them. I also need to somehow move the box just a little bit down so my top panel does not cover it up. Finally, does anybody know if it is possible to show pictures in the weather area. I am using the conkyforecast program for this. Any help would be really appreciated. Thanks in advance.

---

### Post by squaregoldfish on 2009-08-17
Those letters represent a font that contains symbols suitable for displaying icons for the weather and section headings. From the look of your file, you will need two fonts - Openlogos and Weather. If you install these fonts, things will look a whole lot better!

Steve.

---

### Post by ali999 on 2009-08-17
sweet...installing the fonts solved the letter problem and the weather symbol not showing up. Thanks. Any idea on how to move the box a little bit down so that the panel does not cover it though?

---

### Post by ali999 on 2009-08-17
nevermind...figured it out. Need to change the value for gap_y to something larger, then restart conky.

```
# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 5
gap_y 0 # To hide from tranparent window borders.

```

---

