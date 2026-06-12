---
title: "Conky Python conkyBanshee"
date: 2010-08-01
forum: General Help
---

### Post by pippin418 on 2010-08-01
I used to use things like ```
${exec conkyBanshee --datatype=TI}
``` but lot's of those take up way too much memory, so I made a python script to type it all out at once, however I had it print out stuff like ```
${voffset 115}${alignc}%s}
``` the variables show up but it outputs the raw Conky code rather than parsing it. Is there a way to have it parse it?

Python Script
```
import commands
album = commands.getoutput("conkyBanshee --datatype=AL")
title = commands.getoutput("conkyBanshee --datatype=TI")
artis = commands.getoutput("conkyBanshee --datatype=AR")
playt = commands.getoutput("conkyBanshee --datatype=PT")
lengt = commands.getoutput("conkyBanshee --datatype=LE")

print "${voffset 115}${alignc}%s" % album
print "${font DejaVu Sans Mono:size=12}${alignc}${scroll 15 %s }${font}" % title
print "${alignc}%s" % artis
print "${alignc}%s / %s" % (playt, lengt)

```Conky .conkyrc2
```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
# 
 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans Mono:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 10
#update_interval 2 

# Minimum size of text area
# minimum_size 1280 800
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
 
imlib_cache_size 0

# Stippled borders?
stippled_borders 3
 
# border margins
border_margin 9
 
# border width
border_width 10
 
# Default colors and also border colors, grey90 == #e5e5e5
default_color grey
 
own_window_colour brown
own_window_transparent yes
 
# Text alignment, other possible values are commented
alignment bottom_right
#alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
 
# Gap between borders of screen and text
gap_x 10
gap_y 10
 
# stuff after 'TEXT' will be formatted on screen
 
TEXT
${color orange}BANSHEE (${exec conkyBanshee --datatype=ST}) ${hr 2}$color
${exec cp "`conkyBanshee --datatype=CA | sed -e 's/\\\//g'`" /home/kyle/.album}
#-p 80,482 Normal
#-p 80,500 Screw Ups
${image /home/kyle/.album -p 10,22 -s 128x128}
#${voffset 115}${alignc}${exec conkyBanshee --datatype=AL}
#${font DejaVu Sans Mono:size=12}${alignc}${scroll 15 ${execp conkyBanshee --datatype=TI} }${font}
#${alignc}${exec conkyBanshee --datatype=AR}
#${alignc}${exec conkyBanshee --datatype=PT} / ${exec conkyBanshee -d LE}
${exec py ~/banshee.py}
```

---

### Post by pippin418 on 2010-08-01
Ahh, nevermind. ```
${execp py ~/banshee.py}
``` that parses it.

---

