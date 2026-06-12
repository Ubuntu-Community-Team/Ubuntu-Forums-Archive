---
title: "conky borders are weird"
date: 2010-11-28
forum: General Help
---

### Post by bobmatino17 on 2010-11-28
Well, i installed conky, and copied a script from the conkyrc thread, changed the colours a bit, but as ive been using it, ive noticed the borders are strange, they are visible a bit, and i couldnt find a solution to the problem. I have included a copy of my conkyrc and a screenshot.

```
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
minimum_size 400 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders? 8
stippled_borders 0

# border margins 4
border_margin 0

# border width 1
border_width 0

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

own_window_colour white
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text 10
gap_x 0
gap_y 0

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 240}${color #60aaf0}${time %a, } ${color #ffffff}${time %e %B %G}
${offset 240}${color #60aaf0}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color #60aaf0}UpTime: ${color }$uptime
${offset 240}${color #60aaf0}Kern:${color }$kernel
${offset 240}${color #60aaf0}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}${color #60aaf0}Load: ${color }$loadavg
${offset 240}${color #60aaf0}Processes: ${color }$processes  
${offset 240}${color #60aaf0}Running:   ${color }$running_processes

${offset 240}${color #60aaf0}Highest CPU:
${offset 240}${color #dd00bb} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color #60aaf0}Highest MEM:
${offset 240}${color #dd00bb} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color #60aaf0}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color #60aaf0}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color #60aaf0}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color #60aaf0}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}
```

---

### Post by Gillingham on 2010-11-28
Hi I assume you mean the shadowing around the window.  

Using compiz the way I managed it was to add ```
& !(class=Conky)  
```
To the shadow windows using CompizConfig Settings Manager.


 I got this from an earlier forum post by another author.

---

### Post by bobmatino17 on 2010-11-29
Thank you very much, that worked quite nicely.

---

### Post by mugenfanatic on 2011-04-15
I know this is an old thread and all but i've got this same problem and i don't know where i'm suppose to add

& !(class=Conky)

to

---

### Post by WorMzy on 2011-04-15
Install compizconfig-settings-manager, then run

```
ccsm
```

Make sure the Window Decoration plugin is enabled, then click it's name.

[IMG]http://img851.imageshack.us/img851/2439/20110415122201640x323sc.png[/IMG]

The bottom option is where you put the !(class=Conky) option.

---

