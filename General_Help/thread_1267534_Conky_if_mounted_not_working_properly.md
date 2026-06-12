---
title: "Conky if_mounted not working properly"
date: 2009-09-15
forum: General Help
---

### Post by Shpongle on 2009-09-15
Hey all, I have a usb external hd  and it mounts at /media/Iomega HDD

this is the part of my conky.rc that handles that and its not functioning as it should it says not mounted no matter what

${if_mounted /media/Iomega HDD}
External HD:
${fs_used /media/Iomega HDD}/${fs_size /media/Iomega HDD} ${alignr}${fs_bar 8,60 /media/Iomega\ HDD}
${else}External HD: ${alignr}Not Mounted
${endif}


however this works when i have no if statement, it shows when its mounted the used/total space , and when not mounted the same but 0/0 , 
External HD:
${fs_used /media/Iomega HDD}/${fs_size /media/Iomega HDD} 


iv looked around the net and I cant seem to find why its not working. the mount point is right. also i tried \ before the spaces but the second segment of code works in conky without \'s so its not making a difference.

any ideas why its not working , thanks 

Dill

---

### Post by Shpongle on 2009-09-15
I ran conky in the terminal and it says an endif is missing but i only have two if statements in my config and both are closed with endif's  

dill@default:~$ conky
Conky: one or more $endif's are missing


heres my conky.rc

```
# conky configuration
#
# The list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.
#
# For ideas about how to modify conky, please see:
# http://crunchbanglinux.org/forums/topic/59/my-conky-config/
#
# For help with conky, please see:
# http://crunchbanglinux.org/forums/topic/2047/conky-help/
#
# Enjoy! :)
##############################################
#  Settings
##############################################
background yes
# Use Xft?
use_xft yes
xftfont Verdana :size=8
xftalpha 0.8
text_buffer_size 4096

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
    own_window yes
    own_window_transparent yes
    own_window_type desktop
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 200 700
maximum_width 180


# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color white
own_window_colour white

# Text alignment, other possible values are commented
alignment top_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 30
gap_y 15

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
use_spacer none

TEXT
    
SYSTEM ${hr 2}

Kernel:  ${alignr}${kernel}
CPU1: ${cpu cpu1}% ${alignr}${cpubar 8,60 cpu1}
CPU2: ${cpu cpu2}% ${alignr}${cpubar 8,60 cpu2}
RAM: $memperc% ${alignr}${membar 8,60}
Swap: $swapperc% ${alignr}${swapbar 8,60}
Uptime: ${alignr}${uptime}

DATE ${hr 2}
${alignc 35}${font Trebuchet MS:size=26}${time %H:%M}${font}
${alignc}${time %a %d %b %Y}

HD ${hr 2}

Root:
${fs_used /root}/${fs_size /root} ${alignr}${fs_bar 8,60 /root}
${if_mounted /media/Iomega HDD}
External HD:
${fs_used /media/Iomega HDD}/${fs_size /media/Iomega HDD} ${alignr}${fs_bar 8,60 /media/Iomega HDD}
${else}External HD: ${alignr}Not Mounted
${endif}

NETWORK ${hr 2}
${if_existing /proc/net/route wlan0}
Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 789E2D A7CC5C}
Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,60 789E2D A7CC5C}
Uploaded: ${alignr}${totalup wlan0}
Downloaded: ${alignr}${totaldown wlan0}
Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}${else}${if_existing /proc/net/route eth0}
Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,60 789E2D A7CC5C}
Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,60 789E2D A7CC5C}
Uploaded: ${alignr}${totalup eth0}
Downloaded: ${alignr}${totaldown eth0}${endif}${else}${if_existing /proc/net/route eth1}
Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60 789E2D A7CC5C}
Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60 789E2D A7CC5C}
Uploaded: ${alignr}${totalup eth1}
Downloaded: ${alignr}${totaldown eth1}${endif}${else}${font PizzaDude Bullets:size=14}4${font}   Network Unavailable${endif}

PROCESSES ${hr 2}

NAME $alignr PID    CPU
${top name 1} $alignr ${top pid 1} ${top cpu 1}
${top name 2} $alignr ${top pid 2} ${top cpu 2}
${top name 3} $alignr ${top pid 3} ${top cpu 3}
${top name 4} $alignr ${top pid 4} ${top cpu 4}

MUSIC ${hr 2}
${if_running rhythmbox}
Rhythmbox:  ${exec conkyRhythmbox --datatype=ST}
    
Title:  ${scroll 20 ${exec conkyRhythmbox --datatype=TI} } 
Artist:  ${scroll 20 ${exec conkyRhythmbox --datatype=AR} }
Album: ${scroll 20 ${exec conkyRhythmbox --datatype=AL} }
Position:  ${scroll 20 ${exec conkyRhythmbox --datatype=PT}/${exec conkyRhythmbox --datatype=LE}}
${else}
Rhythmbox: Not Playing
${endif} 

```

---

### Post by Shpongle on 2009-09-16
i tried to check if a cdrom0  with a cd was mounted instead and it worked so it must be something to do with the space at the mount point,

iv tried ${if_mounted /media/Iomega HDD}
${if_mounted "/media/Iomega HDD"}
${if_mounted /media/Iomega\ HDD}

and

${if_mounted /media/"Iomega HDD"}

also ran df and found it was at /dev/sdb1


dill@default:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            113314052  51600344  55957624  48% /
tmpfs                  1026164         0   1026164   0% /lib/init/rw
varrun                 1026164       232   1025932   1% /var/run
varlock                1026164         0   1026164   0% /var/lock
udev                   1026164       160   1026004   1% /dev
tmpfs                  1026164       196   1025968   1% /dev/shm
lrm                    1026164      2192   1023972   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sdb1            976760000 220497736 756262264  23% /media/Iomega HDD
dill@default:~$

it has to be the name of it, thats the only thing i can think of

---

### Post by Shpongle on 2009-09-16
any ideas?

---

