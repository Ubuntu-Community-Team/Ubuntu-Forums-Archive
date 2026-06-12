---
title: "Conky Overlapping Everything"
date: 2010-06-30
forum: General Help
---

### Post by windowsmediaman on 2010-06-30
Conky seems to be overlapping everything.
[http://i50.tinypic.com/2irazia.jpg](http://i50.tinypic.com/2irazia.jpg)
SO I don't know why but to add it to the start up I just did conky in all options is there a way to do it that won't do this I read a couple threads and it says there was but I couldn't figure out how. I am very nooby so please break it down for me. 
I figured out the way to fix tempararlily is to go into the conky edit menu using teminal and click save then it fixes or to just restart conky. That gets annoying having to do that every startup of the computer.
Thanks for any help.

---

### Post by windowsmediaman on 2010-06-30
No replies... If there is none I will just go to another forum.

---

### Post by SoFl W on 2010-06-30
okay....

but perhaps you can show your conky.rc file.  That would help.

---

### Post by windowsmediaman on 2010-06-30
> # conky configuration
# edited by Mark Buck (Kaivalagi) <m_buck@hotmail.com>

# set to yes if you want Conky to be forked in the background
background Yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=9

# Text alpha when using Xft
xftalpha 0.8

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 300 0
maximum_width 300

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no
draw_graph_borders yes

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# own window options
own_window        yes
own_window_transparent    yes
own_window_type        override
own_window_hints    undecorated,below,sticky,skip_taskbar,skip_pager

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 35

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

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer right

# colours
color1 white
# light blue
color2 6892C6
# orange
#E77320
color3 FC8820
# green
color4 78BF39
# red
color5 CC0000

text_buffer_size 2048

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
${color3}${voffset -6}${font Bitstream Vera Sans Mono:style=Bold:size=11}System${font}  ${hr}${color1}

${font}${color3}  Uptime: ${alignr}${color1}${uptime}
${color3}  Kernel: ${alignr}${color1}${kernel}

${font}${color3}  AC Adapter: ${alignr}${color1}${acpiacadapter}
${font}${color3}  Battery: ${alignr}${color1}${battery BAT0}
${font}${color3}  Time left: ${alignr}${color1}${battery_time BAT0}

${font}${color3}  Temp: ${alignr}${offset 5}${color1}${execi 6 /usr/bin/sensors | grep temp1 | paste -s | cut -c15-22}

${font}${color3}  CPU 1: ${alignr}${color1}${cpu cpu1}% ${cpugraph cpu1 7,80 FFFFFF FFFFFF}
${font}${color3}  CPU 2: ${alignr}${color1}${cpu cpu2}% ${cpugraph cpu2 7,80 FFFFFF FFFFFF}
${font}${color3}  RAM: ${alignr}${color1}${memperc}% ${membar 5,80}
${font}${color3}  SWAP: ${alignr}${color1}$swapperc% ${swapbar 5,80}

${font}${color3}  Boot:
${color1}   ${fs_used /boot} / ${fs_size /boot} ${alignr}${fs_bar 5,80 /boot}
${font}${color3}  Root:
${color1}   ${fs_used /} / ${fs_size /} ${alignr}${fs_bar 5,80 /}
${font}${color3}  Home:
${color1}   ${fs_free /home} / ${fs_size /home} ${alignr}${fs_bar 5,80 /home}
${font}${color3}  Video:
${color1}   ${fs_free /home/stancho/Videos} / ${fs_size /home/stancho/Videos} ${alignr}${fs_bar 5,80 /home/stancho/Videos}

${color3}${voffset -6}${font Bitstream Vera Sans Mono:style=Bold:size=11}Gmail Messages${font}  ${hr}${color1}

You have ${color3}${texeci 60 perl ~/scripts/gmail.pl n} ${color}new gmail(s).
${execi 60 perl ~/scripts/gmail.pl s}
There you go.

---

### Post by michaelgilch on 2010-07-01
By any chance, do you use ubuntu-tweak? I had the same thing happening and it ended up being an ubuntu-tweak setting for not showing icons on the desktop that was causing it.

Also, does conky run on startup. It may be starting up too soon, before compiz starts fully. You can try adding: sleep 10; conky to the startup applications.

---

### Post by themusicalduck on 2010-07-01
I have a script to startup conky with a delay. Just save this as a text file with .sh on the end and then select it in startup applications.

```
#!/bin/bash
sleep 30 && conky ;
```

---

### Post by sevenearths on 2011-11-11
> **themusicalduck said:**
> I have a script to startup conky with a delay. Just save this as a text file with .sh on the end and then select it in startup applications.

```
#!/bin/bash
sleep 30 && conky ;
```

Thanks. This had been bugging me for hours

---

### Post by |Anthony| on 2011-12-19
you have 2 instances of own_window. Comment out the one that says own_window False
also, you have own_window_type override which ignores all window hints such as below.
change own_window_type override to own_window_type normal and see what happens.

---

### Post by Frogs Hair on 2011-12-19
I agree with   |Anthony| and the following  are also options to try .  ```
own_window_type conky
``````
own_window_type desktop
```

---

### Post by |Anthony| on 2011-12-21
> **Frogs Hair said:**
> the following  are also options to try .  ```
own_window_type conky
``````
own_window_type desktop
```
 

Setting own_window_type conky will default to own_window_type normal

Check [http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html) to see all available own_window_type options.

Side note: own_window_type desktop sets conky in the desktop layer (i believe) and as such gets pushed under your desktop background. At least it did for me when i was poking around.

---

