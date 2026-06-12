---
title: "after upgrading from 9.04 to 10.04 Conky no longer displays."
date: 2011-04-23
forum: General Help
---

### Post by sefs on 2011-04-23
Hi all,

After upgrading from 9.04 to 10.04 Conky no longer displays as it used to.

I believe it has something to do with own_window_type set to override.  If I change this to desktop, dock, or normal it displays. 

Conky starts without any errors but just does not display anything.

The best lead I had thus far was that it was something in ~/.cache, but even after deleting that and having it recreated still no cigar.

Is there anything else I should be looking at?

Thanks.

---

### Post by ajgreeny on 2011-04-23
Show us the .**conkyrc** file in your home and it may be possible to help more.

---

### Post by sefs on 2011-04-23
> **ajgreeny said:**
> Show us the .**conkyrc** file in your home and it may be possible to help more.

Here it is....

```

# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background yes

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
#xftfont Bitstream Vera Sans Mono:size=8
#xftfont verdana:size=8
xftfont Monospace:size=9

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 5.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
#own_window_colour black

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
stippled_borders 0

# border margins
#border_margin 4
border_inner_margin 4

# border width
border_width 0

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
# gap_x 12
# gap_y 12
gap_x 0
gap_y 24

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

# Add spaces to keep things from moving about?  This only affects certain objects.
#use_spacer no
use_spacer none

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 256

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
#max_user_text 16384

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

# $nodename - $sysname $kernel on $machine
TEXT
${color white}Kernel - $sysname $kernel on $machine
${color white}$stippled_hr
${color white}Uptime:$color $uptime ${color white}- Load:$color $loadavg
${color white}$stippled_hr
Performance:
 ${color white}CPU Usage:${color #ddaa00} $cpu% 
 ${cpubar}
 ${color white}RAM Usage:$color $mem/$memmax - $memperc% 
 ${membar}
 ${color white}Swap Usage:$color $swap/$swapmax - $swapperc% 
 ${swapbar}
${color white}$stippled_hr
${color white}Networking:
 ${color white}LAN:                    ${color white}WIFI:
 ${color white}Down:${color #7cfc00}${goto 50}${downspeedf eth0}${goto 100}k/s${goto 180}${color white}Down:${color #7cfc00}${goto 220}${downspeedf wlan0}${goto 270}k/s    
 ${color white}Up  :${color #ddaa00}${goto 50}${upspeedf eth0}${goto 100}k/s${goto 180}${color white}Up  :${color #ddaa00}${goto 220}${upspeedf wlan0}${goto 270}k/s    
${color white}$stippled_hr
${color white}File systems:
 root $color${fs_used /}/${fs_size /} 
 ${fs_bar /}
 home $color${fs_used /home}/${fs_size /home} 
 ${fs_bar /home}
${color white}$stippled_hr
${color white}Processes:$color $processes  ${color grey}Running:$color $running_processes
${color white}$stippled_hr
${color white}Name                     PID   CPU%   MEM%
${color #ddaa00} ${top name 1}       ${top pid 1} ${top cpu 1} ${top mem 1}
${color white} ${top name 2}       ${top pid 2} ${top cpu 2} ${top mem 2}
${color white} ${top name 3}       ${top pid 3} ${top cpu 3} ${top mem 3}
${color white} ${top name 4}       ${top pid 4} ${top cpu 4} ${top mem 4}
${color white} ${top name 5}       ${top pid 5} ${top cpu 5} ${top mem 5}
${color white}$stippled_hr

```


output from terminal:
```

$conky -d -c ~/.conkyrc &
[1] 4085
$ Conky: forked to background, pid is 4086

Conky: desktop window (2800003) is subwindow of root window (102)
Conky: window type - override
Conky: drawing to created window (0x4c00001)
Conky: drawing to double buffer

[1]+  Done                    conky -d -c ~/.conkyrc

```

---

### Post by sefs on 2011-04-24
Ok. Conky is back again.

It re-appeared after I chose the recovery option in the boot menu, and let it do it's thing.  Then after a regular reboot conky was there again.  So I am not sure if some sort of fs corruption was preventing it from displaying with the override switch.

---

### Post by sefs on 2011-04-27
Seems like I spoke too soon ... the problem is still there.  conky is clearly starting but its not displaying anything at all from .conkyrc.  And it seems to do this when window_type is override

---

### Post by sefs on 2011-04-27
Ok, I think I have sorted this thing out.  I had to do two things and now it looks like it is stably loading on boot.

1/ Delete all files in ~/.cache/sessions

2/ On shut down un-check the "Save session for future log on" checkbox in the shutdown dialog screen.

... and that seems to be the size of it.  I am not too sure what would happen if I re-enable the checkbox as yet. Will test that over the next days.

---

