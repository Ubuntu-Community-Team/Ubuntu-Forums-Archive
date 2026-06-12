---
title: "Something similar  to &quot;mkconsole&quot; for Mac?"
date: 2009-11-21
forum: General Help
---

### Post by kartal on 2009-11-21
Hi

Does anyone know any software similar to "mkconsole" [http://www.mulle-kybernetik.com/software/MkConsole/](http://www.mulle-kybernetik.com/software/MkConsole/) ?


I have tried Conky to display some text files but I am neither having any fun  nor having any success. My desktop display is  either not updated or truncated(very small portion of the text is shown). I tried various text diplaying methods that are propvided by conky but I am not getting it working well.

 I just want to display some text files(small or large) on my desktop


thanks

---

### Post by yeeeev on 2009-11-23
Here's a conky script that will tail some logs onto the desktop. 
You need to place it as /home/{you}/.conkyrc
After that you simply run conky

---

### Post by yeeeev on 2009-11-23
Upload didn't work, so:

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
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 3.0
 
# Minimum size of text area
# minimum_size 250 5
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
 
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
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
 
# Gap between borders of screen and text
gap_x 10
gap_y 20
 
# stuff after 'TEXT' will be formatted on screen
 
TEXT
$color
${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}

---

### Post by kartal on 2009-11-25
Hi
Sorry for the late follow up. Thanks for the config. I will try it today. 

thanks

---

