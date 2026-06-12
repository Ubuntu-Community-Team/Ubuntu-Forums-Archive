---
title: "conky disappears when i click desktop &amp; cant close terminal"
date: 2010-09-30
forum: General Help
---

### Post by fuzzylogic25 on 2010-09-30
I just installed conky and ran the command:

John@cmp:~/Apps/Conky$ conky -c /etc/conky/conky.conf
Conky: desktop window (1a000a9) is subwindow of root window (1ad)
Conky: window type - desktop
Conky: drawing to created window (0x3200001)
Conky: drawing to single buffer



It just stays there and the terminal cant be used. How can you change it so you can still use the terminal?

Also, when i click the desktop the conky screen disappears forever. Why is this so?

---

### Post by ajgreeny on 2010-09-30
Firstly, you should to start conky by using Alt+F2, not terminal; that will solve your terminal always open problem.

Secondly you need to make a better config file, rather than the one used at the moment, which is there as an example, not actually to be used in most situations.  There are three lines in your conky.conf
```
own_window yes
own_window_class Conky
own_window_type desktop
``` which to stop the window disappearing need to be
```
# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes
``` I have left in the comments to show you how most config files look.

This code is from my own configuration file which by default is named .conkyrc and sits in my home folder/partition.  If a file of this name exists in your home, conky will use it with no further action on your part, and conky be started at boot with the single command **conky**, no need to tell it where the config file is.  I do it this way, the only problem being the need to start it at boot time with a shell script to make it wait 10 seconds before starting with the sleep command
```
#!/bin/bash
sleep 10;conky
``` Make this executable, and then point to it in **System ->Preferences ->Startup Applications** and a few seconds after your desktop appears, conky will pop up.  You can also do thios more simply by just using the command ```
bash -c "sleep 10; conky"
``` in the Startup Applications command box, exactly as I show it with the " " marks.

Here is my .conkyrc to give you a start.  There are masses of other examples available in other places, as well as in this forum, but mine is relatively simple.
```
# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Trebuchet MS:size=10

# Text alpha when using Xft
xftalpha 0.9

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 220

# Maximum width
maximum_width 220

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
# stippled_borders 8

# border margins
# border_margin 2

# border width
# border_width 1

# Default colors and also border colors
default_color white
default_shade_color red
default_outline_color green

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 25
gap_y 50

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# variable is given either in format $variable or in ${variable}

# stuff after 'TEXT' will be formatted on screen

TEXT
${font Trebuchet MS:size=30} ${alignc}${time %k:%M}
${font Trebuchet MS:size=20} ${alignc}${time %a %b %d %Y}${font Trebuchet MS:size=10}

${color #EFEBE6}Hostname:${color #DE0084}$alignr$nodename
${color #EFEBE6}Uptime:${color #DE0084}$alignr$uptime

${color #EFEBE6}CPU ${color #DE0084}${cpu cpu1}% ${color #EFEBE6}${cpubar cpu1}
${color #EFEBE6}Processes: ${color #DE0084}$processes ${alignr}Running: $running_processes
#
#${color #EFEBE6}CPU Usage        ${color #DE0084} $alignr PID   CPU%   MEM%
#${color #EFEBE6} ${top name 1} ${color #DE0084} $alignr ${top pid 1}  ${top cpu 1}  ${top mem 1}

${color #EFEBE6}sda1
${color #EFEBE6} Root ${color #DE0084}${fs_used_perc /}% ${color #EFEBE6}${fs_bar /}
$alignr ${color #DE0084}${fs_used /}/${fs_size /}
${color #EFEBE6}sda2
${color #EFEBE6} Home ${color #DE0084}${fs_used_perc /home}% ${color #EFEBE6}${fs_bar /home}
$alignr ${color #DE0084}${fs_used /home}/${fs_size /home}

${color #EFEBE6}RAM Usage:
$alignr${color #DE0084}$mem of $memmax ${color #DE0084}= ${color #DE0084}$memperc%  

${color #EFEBE6}Swap: ${color #DE0084}$swapperc% ${color #EFEBE6}${swapbar}
${color #DE0084} ${alignr}$swap of $swapmax

${color #EFEBE6}NETWORK IP:${color #DE0084} $alignr eth0 -  ${color #DE0084}${addr eth0}

${color #EFEBE6}DOWN:${color #DE0084} ${downspeed eth0}/s ${color #EFEBE6}$alignr TOTAL ${color #DE0084}${totaldown eth0}
${color #EFEBE6}${downspeedgraph eth0 30,220 000000 #EFEBE6}

${color #EFEBE6} Up:${color #DE0084} ${upspeed eth0}/s ${color #EFEBE6}$alignr TOTAL ${color #DE0084}${totalup eth0}
${color #EFEBE6}${upspeedgraph eth0 30,220 000000 #EFEBE6}

```I hope this helps.

---

### Post by fuzzylogic25 on 2010-09-30
Thank you so much for that post! I used yours and got it all working perfect.

I like your set up too, but ill prob add some more stuff to it like CPU temp, and individual CPU usage. I just wanted to ask, how do you increase the font on it? I have looked through your config but nothing seems to show that?

---

### Post by Quackers on 2010-09-30
As ajgreeny seems to be offline at the moment the font size is here in his conkyrc file
```
# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Trebuchet MS:size=10

```

Size 10, to make it bigger just increase to 12 or 14, whatever.

---

