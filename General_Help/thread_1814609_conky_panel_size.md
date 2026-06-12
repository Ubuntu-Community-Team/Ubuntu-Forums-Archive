---
title: "conky panel size"
date: 2011-07-29
forum: General Help
---

### Post by chris1497 on 2011-07-29
How do you change the size of the panel? I've looked through each line of my .conkyrc but can't find anything.  I'd like to make it a thin panel that strecthes vertically down the right side of my screen 100x1000.  For some reason it seems to be locked into the default size though - 300x600ish.  I've looked at numerous other .conkyrc files (such as below) and it appears they do not have this limitation or anything obvious that allows them to have something different from the default.

Is there another config file that sets the size of the panel?

[HTML]http://dotshare.it/dots/128/[/HTML]

---

### Post by chris1497 on 2011-07-29
using minimum_size
maximum_size
maximum_width

do not work.  Is there some other config file superseding these settings?

---

### Post by runesvend on 2012-04-29
So how did you solve this?

---

### Post by chris1497 on 2012-04-30
Don't recall. It might've fixed when I properly restarted conky. It might've been the own window thing. Sorry I can't give you more at the moment.

here's my config file:

```

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no
own_window_type override #doesn't minimize with super+D


# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
minimum_size 100 1200
#minimum_size  1050 #useless
#maximum_width 1050 #useless

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
#border_margin 4

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
gap_x 0
gap_y 0

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

###################################################################3

TEXT
#############
###########


${time %H:%M:%S}      ${time %a, } ${color }${time %e } 
#%B }${color }
########
#${color slate grey}${time %Z,    }
${color slate grey}Volume: ${color }${mixer}%
${color slate grey}UpTime: ${color }$uptime
#${color slate grey}Kern:${color }$kernel
${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${cpugraph 20,130 000000 ffffff}
${color slate grey}Load: ${color }$loadavg
${color slate grey}Processes: ${color }$processes  
${color slate grey}Running:   ${color }$running_processes
####################
${color slate grey}Highest CPU:
${color #007EBD}${top pid 1}  ${top name 1}${top_mem cpu 1}
${color lightgrey}${top pid 2}  ${top name 2}${top cpu 2}
${color lightgrey}${top pid 3}  ${top name 3}${top cpu 3}
${color lightgrey}${top pid 4}  ${top name 4}${top cpu 4}
#####################
${color slate grey}Highest MEM:
${color #007EBD}${top_mem pid 1}  ${top_mem name 1}${top_mem mem 1}
${color lightgrey}${top_mem pid 2}  ${top_mem name 2}${top_mem mem 2}
${color lightgrey}${top_mem pid 3}  ${top_mem name 3}${top_mem mem 3}
${color lightgrey}${top_mem pid 4}  ${top_mem name 4}${top_mem mem 4}
 
${color slate grey}RAM ${color }${membar 3,100}
${color } $memperc%  $mem / ${color lightgrey}$memmax
${color slate grey}SWAP ${color }${swapbar 3,100}
${color }$swapperc%  $swap / ${color lightgrey}$swapmax
####
${color slate grey}ROOT ${color }${fs_bar 3,100 /}
${color #007EBD}${fs_free /} / ${color lightgrey}${fs_size /}
${color slate grey}MYDAT ${color }${fs_bar 3,100 /media/8E026AF7026AE3A5}${color }
${fs_free /media/8E026AF7026AE3A5} / ${color lightgrey}${fs_size /media/8E026AF7026AE3A5}
#
#${color slate grey}FA drive:  ${color }${fs_free /media/FreeAgent\ Drive}/${fs_size /media/FreeAgent\ Drive}
#${fs_bar 3,100 /media/FreeAgent\ Drive}
#
#
#${color slate grey}SLACK:  ${color }${fs_free /mnt/slack}/${fs_size /mnt/slack}
#${fs_bar 3,100 /mnt/slack}
####################################
#${color4}${font Terminus:style=Bold:size=14}@ ${font Terminus:style=Bold:size=11}Rhythmbox${font}
#${color4}Template Output:
###
#${color1}${execp conkyRhythmbox --template=/home/chris/Desktop/chris/conkyRhythmbox.template}
###
#${color4}Standard Output:
#${voffset 5}${color4} Title:  ${color1}${font}${exec conkyRhythmbox --datatype=TI} 
#${color4} Position:  ${color1}${font}${exec conkyRhythmbox --datatype=PT}/${exec conkyRhythmbox --datatype=LE}

${color slate grey}Keybindings
${color }${execi 240 cat /home/chris/Dropbox/other/lists/vimkeybinding.txt}

#${color }${execi 240 cat /home/chris/Dropbox/other/lists/mckeybinding.txt}

###
#${color orange}RSS feed ${hr 2}$color 
#${execi 300 /home/chris/Desktop/conky-rss.sh}
###
#${image ~/Dropbox/formulas.png -p 0,570 }#-s 32x32 }
##########################################################
#Banshee${hr 2}
#${exec banshee-1 --query-artist}
#${exec banshee-1 --query-title}
##########################################################
#
#ETHERNET eth0: ${addr eth0}
#
#${addr wlan0}  
#essid: ${wireless_essid wlan0}
#signal: ${wireless_link_bar 8,70 wlan0}

```

---

### Post by matthewglen on 2013-01-06
I just ran into this same issue, and it was fixed by killing and restarting conky.

---

