---
title: "conky flickers, transparent ?"
date: 2010-02-03
forum: General Help
---

### Post by elementxyz on 2010-02-03
Hi,

i searched the forum but don't find an answer. I set up my conky rc and recognized that my icons disapear. After a little time of search i copy these lines in my conkrc:

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

the "problem" for me is now every 2 seconds when conky updates itself
you see a little black box arround my conky.

What should i do ???

---

### Post by proxess on 2010-02-03
double_buffer yes
own_window yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
own_window_transparent yes
own_window_type override

border_inner_margin 0
border_width 0
draw_borders no
draw_shades no
stippled_borders 0

---

### Post by elementxyz on 2010-02-03
ok, thanks it's better now! But still have the black background not every 2 seconds but it's there. I think my gma950 is to slow because the driver from intel is not so good.

---

### Post by proxess on 2010-02-03
Intel drivers are perfectly fine.

Show me your conkyrc.

---

### Post by elementxyz on 2010-02-08
here is my conkyrc. 



# conky configuration
# edited by maz

# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=8
xftfont NeutraText-Demi:size=10

# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
# out_to_console no

# Update interval in seconds
update_interval 2.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 10 5

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_inner_margin 0

# border width
border_width 0

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# Text alignment, other possible values are commented
alignment top_right


# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 20
gap_y 998

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
override_utf8_locale no

# stuff after 'TEXT' will be formatted on screen

TEXT
${offset 1}${color #e04613} ${color}${time %H:%M}  | ${offset 1}${color #e04613} ${color}${time %a, } ${time %e %B %G} | ${offset 1}${color #e04613}UpTime: ${color }$uptime

---

### Post by cccc on 2011-04-24
Here is my conky config and I have no flickering under Gnome:```

background yes

alignment top_right
gap_x 75
gap_y 70

use_xft yes
xftfont Sans:size=8
xftalpha 1
text_buffer_size 2048

update_interval 3.0
total_run_times 0

double_buffer yes

own_window yes
own_window_transparent yes
own_window_type normal
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

minimum_size 5 5
maximum_width 200

draw_shades yes
draw_outline no
draw_borders no

border_width 0
border_inner_margin 0
border_margin 0
stippled_borders 0

default_color white
default_shade_color black
default_outline_color white

no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
use_spacer yes
override_utf8_locale no


TEXT
${font sans-serif:bold:size=8}SYSTEM ${hr 2}
${font sans-serif:normal:size=8}Kernel:  ${alignr}${kernel}
Host:$alignr$nodename
CPU: ${cpu cpu}% ${alignr}${cpubar 8,60 cpu}
RAM: $memperc% ${alignr}${membar 8,60}
Uptime: ${alignr}${uptime}

${font sans-serif:bold:size=8}MEMORY ${hr 2}
${font sans-serif:normal:size=8}RAM $alignc $mem / $memmax $alignr $memperc%
$membar
SWAP $alignc ${swap} / ${swapmax} $alignr ${swapperc}%
${swapbar}

${font sans-serif:bold:size=8}NETWORK ${hr 2}
IP address: $alignr ${addr eth0}

```

---

