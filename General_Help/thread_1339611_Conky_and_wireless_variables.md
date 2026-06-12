---
title: "Conky and wireless variables"
date: 2009-11-27
forum: General Help
---

### Post by geco0ol on 2009-11-27
Hello

Somebody, please help
I have downloaded and compiled conky v1.7.2 everythign ok, but i stil cannot access wireless variables. they either return nothing or 0 values, even if the wireless link is up and running. 
Below is my .conkyrc

# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
#minimum_size 400 5

maximum_width 300
# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 20}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 20}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 20}${color slate grey}UpTime: ${color }$uptime
${offset 20}${color slate grey}Kern:${color }$kernel
${offset 20}${color slate grey}Temperatura core: ${acpitemp}C
${offset 20}${color slate grey}CPU0:${color } ${cpu cpu1}% ${freq_g 1}GHz
${offset 20}${cpugraph 0 20,130 000000 ffffff}
${offset 20}${color slate grey}CPU1:${color } ${cpu cpu2}% ${freq_g 1}GHz
${offset 20}${cpugraph 1 20,130 000000 ffffff}
${offset 20}${color slate grey}Load: ${color }$loadavg
${offset 20}${color slate grey}Processes: ${color }$processes  
${offset 20}${color slate grey}Running:   ${color }$running_processes

${offset 20}${color slate grey}Highest CPU:
${offset 20}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 20}${color lightgrey} ${top name 2}${top cpu 2}
${offset 20}${color lightgrey} ${top name 3}${top cpu 3}
${offset 20}${color lightgrey} ${top name 4}${top cpu 4}

${offset 20}${color slate grey}Highest MEM:
${offset 20}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 20}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 20}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 20}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 20}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 20}${membar 3,100}
${offset 20}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 20}${swapbar 3,100}

${offset 20}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 20}${fs_bar 3,100 /}
${offset 20}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 20}${fs_bar 3,100 /home}
${offset 20}${color slate grey}SLACK:  ${color }${fs_free /mnt/slack}/${fs_size /mnt/slack}
${offset 20}${fs_bar 3,100 /mnt/slack}
${offset 20}${color slate grey}NET: 
${offset 20}${color}Up: ${color }${upspeed eth2}
${offset 20}${upspeedgraph eth2 20,130 FF0000 00ff00}
${offset 20}${color}Down: ${color }${downspeed eth2}
${offset 20}${downspeedgraph eth2 20,130 FF0000 00ff00}

${offset 20}Wireless: ${wireless_essid eth2}
${offset 20}${wireless_link_bar 10,200 eth2}

${offset 20}${color slate grey}Baterie: $battery $battery_percent %
#${offset 20}${battery_bar 10, 200 0}

I want to see wireless specific stuff, but it won;t work. please help !

---

