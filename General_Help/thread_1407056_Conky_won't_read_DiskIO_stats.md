---
title: "Conky won't read DiskIO stats"
date: 2010-02-14
forum: General Help
---

### Post by mechgt on 2010-02-14
Conky stopped reading Disk IO stats... it just reads 0.  It used to work in Hardy, but I upgraded to Jaunty and it stopped working.  It's monitoring an mdadm raid array, and I had a few problems with that during the upgrade also, but it's all working OK now (it tried to assign to something other than md0, fixed now).  I've searched and haven't seen this problem with anyone else.  This same file works on one computer upstairs, but not the other.  The non-working computer is Jaunty, the working computer is Karmic, and they were both working on Hardy.  The non-working computer is monitoring an mdadm raid array, and the working computer is monitoring a regular single disk.  Any ideas?

Below is my conky file with the problem part **BOLDED** near the bottom:

```
# THIS CONFIG RELIES ON 2 SCRIPTS, CPUSPEED AND CPUTEMP
# YOUR SYSTEM MAY NOT REQUIRE THEM, REPLACE AS DESIRED

# maintain spacing between certain elements
use_spacer none

# set to yes if you want conky to be forked in the background
background no

use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono-7
#xftfont Andale Mono-9
#xftfont Clean-8
#xftfont cubicfive10:pixelsize=8
#xftfont squaredance10:pixelsize=14
#xftfont swf!t_v02:pixelsize=10

# Text alpha when using Xft
xftalpha 1
mail_spool $MAIL

# Update interval in seconds
update_interval 4.0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar
background yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no # amplifies text

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 9

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey90
default_shade_color black
default_outline_color DarkGrey
# Title (OS, etc)
color0 828282
# Header 1, 2, 3 (data)
color1 ffcb48
color2 aaccee
color3 e5e5e5
# Graphs
color4 b59d59
#color4 b3defd
color5 a3a3a3
# Process Colors (light -> dark)
color6 fdd99b
color7 e9cb8a
color8 cfb472
color9 b59d59

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right

# Gap between borders of screen and text
gap_x 24
gap_y 24

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# stuff after 'TEXT' will be formatted on screen

TEXT
${color1}$nodename${color3}      ${color0}$sysname $kernel on $machine${color3}
   ${color2}SYSTEM UPTIME:${color3}  $uptime
${color1}PROCESSING
   ${color4}$cpubar
   ${color4}${cpugraph 78af78 a3a3a3}

   ${color2}NAME             PID       CPU%      MEM%
   ${color6}${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
   ${color7}${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
   ${color8}${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
   ${color9}${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color1}DATA
   ${color2}RAM:${color3}  $memperc%         ${color4}${membar 6}
   ${color2}Swap:${color3} $swapperc%         ${color4}${swapbar 6}

   ${color2}NAME             PID       CPU%      MEM%
   ${color6}${top_mem name 1} ${top_mem pid 1}   ${top_mem cpu 1}     ${top_mem mem 1}
   ${color7}${top_mem name 2} ${top_mem pid 2}   ${top_mem cpu 2}     ${top_mem mem 2}
   ${color8}${top_mem name 3} ${top_mem pid 3}   ${top_mem cpu 3}     ${top_mem mem 3}
   ${color9}${top_mem name 4} ${top_mem pid 4}   ${top_mem cpu 4}     ${top_mem mem 4}

   ${color2}/:${color3}    ${fs_used_perc /}% $fs_free ${color4}${fs_bar 6 /}
   ${color2}Raid:${color3} ${fs_used_perc /media/raid}% ${fs_free /media/raid} ${color4}${fs_bar 6 /media/raid}
   [B]${color4}${diskiograph /dev/md0 42,262 78af78 a3a3a3}
   ${color2}Disk I/O:${color3}  ${diskio /dev/md0}
   ${color2}Write:${color3} ${diskio_write /dev/md0}${color2} Read: ${color3}${diskio_read /dev/md0}${color2} Total:${color3} ${diskio /dev/md0}[/B]

   ${color2}Upload:${color3}   ${upspeed eth2}kb/s  ${totalup eth2}
   ${color2}Download:${color3} ${downspeed eth2}kb/s  ${totaldown eth2}



```

Here's a screenshot of the problem area:
[[IMG]http://img180.imageshack.us/img180/4185/conky2000.png[/IMG]](http://img180.imageshack.us/i/conky2000.png/)

---

