---
title: "Please can someone make or help me"
date: 2010-06-19
forum: General Help
---

### Post by localguy on 2010-06-19
Hello,

can someone please make me a auto startup file for my conky? and tell me where to place that file? i been trying couple days and still cant get it to work :(

i even added it to Startup Applications and still nothing /usr/bin/conky

Thanks for reading and the help

---

### Post by ajgreeny on 2010-06-19
It will simply need a shell script
```
#!/bin/bash
sleep 20; conky
```Copy this to an empty text file in gedit, save it as **conky-delay.sh** in your home, then make it executable by right clicking the file in nautilus, choosing Properties-Permissions tab and checking the "Allow executing file as program" box.  Now in your startup applications dialog window just point to that script (/home/*username*/conky-delay.sh), and it should work.

You will also need a** .conkyrc** file in your home as the configuration for what you want to appear in the conky window.  There are lots of examples on the net and in this forum to get you going if you do not already have one.

By the way you need the **sleep 20;** in the script to allow gnome to start properly before conky or it will not display properly.  The sleep just means the **conky** command is not actually run for 20 seconds after the script runs.

---

### Post by localguy on 2010-06-19
> **ajgreeny said:**
> It will simply need a shell script
```
#!/bin/bash
sleep 20; conky
```Copy this to an empty text file in gedit, save it as **conky-delay.sh** in your home, then make it executable by right clicking the file in nautilus, choosing Properties-Permissions tab and checking the "Allow executing file as program" box.  Now in your startup applications dialog window just point to that script (/home/*username*/conky-delay.sh), and it should work.

You will also need a** .conkyrc** file in your home as the configuration for what you want to appear in the conky window.  There are lots of examples on the net and in this forum to get you going if you do not already have one.

By the way you need the **sleep 20;** in the script to allow gnome to start properly before conky or it will not display properly.  The sleep just means the **conky** command is not actually run for 20 seconds after the script runs.

Hi ok im at the save point **conky-delay.sh** but its giving me an error **Could not save the file /home/conky-delay.sh. You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.**

also i was about to post a new problem when i do start conky my icons i have on desktop dissapear, if i drag my mouse like highighting them they blink then dissapear.. i will post my conky codes in here maybe you or someone might know why?


```
 # Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel artwiz package?
#font 5x8
#font 6x9
font 6x10
#font 6x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# Use Xft?
use_xft no

# Set conky on the bottom of all other applications
on_bottom yes

# Xft font when Xft is enabled
xftfont Gothic:size=8

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
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour grey

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline yes

# Draw borders around text
draw_borders no



# border margins
border_margin 4



# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 65

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase yes

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
Uptime:${color lightgrey} $uptime $color
with ${color lightgrey}$sysname $color $kernel on $machine
Current Time ${time %I:%M %P}
${color lightgrey}HDD I/O:$color $diskio
${color red}${diskiograph 0000ff 00ff00}
${color lightgrey}CPU Usage:$color $cpu% ${color #cc2222} ${cpubar}
${color red}${cpugraph 0000ff 00ff00}
${color lightgrey}RAM Usage:$color $mem/$memmax - $memperc% ${membar}
${color lightgrey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar}
${color lightgrey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$color$stippled_hr
${color limegreen} Temperature: ${color red} ${acpitemp} ${color lightgrey}  ${acpifan}
$color$stippled_hr
${color lightgrey}File systems:$color
 root  $color${fs_used /}  /${fs_size /} ${fs_bar /}
 home  $color${fs_used /home} /${fs_size /home} ${fs_bar /home}
 fat32 $color${fs_used /media/fat32}  /${fs_size /media/fat32} ${fs_bar /media/fat32}
$color$stippled_hr
${color}CPU Usage:        CPU%   MEM%   PID
${color #ff4500} ${top name 1} ${top cpu 1} ${top mem 1} ${top pid 1}
${color #eeee00} ${top name 2} ${top cpu 2} ${top mem 2} ${top pid 2}
${color #00ee00} ${top name 3} ${top cpu 3} ${top mem 3} ${top pid 3}
${color lightgrey} ${top name 4} ${top cpu 4} ${top mem 4} ${top pid 4}
${color lightgrey} ${top name 5} ${top cpu 5} ${top mem 5} ${top pid 5}
$color$stippled_hr
${color}MEM usage:
${color #ff4500} ${top_mem name 1} ${top_mem cpu 1} ${top_mem mem 1} ${top_mem pid 1}
${color #eeee00} ${top_mem name 2} ${top_mem cpu 2} ${top_mem mem 2} ${top_mem pid 2}
${color #00ee00} ${top_mem name 3} ${top_mem cpu 3} ${top_mem mem 3} ${top_mem pid 3}
${color lightgrey} ${top_mem name 4} ${top_mem cpu 4} ${top_mem mem 4} ${top_mem pid 4}
${color lightgrey} ${top_mem name 5} ${top_mem cpu 5} ${top_mem mem 5} ${top_mem pid 5}
$color$stippled_hr
${color lightgrey}Networking:${color #00ee00} PPP0 ${color lightgrey} on $color ${addr ppp0}
${color lightgrey} Down:${color #8844ee} ${downspeedf ppp0} k/s${color lightgrey} ${offset 80}Up:${color #22ccff} ${upspeedf ppp0} k/s
${color #0000ff}${downspeedgraph ppp0 22,150 ff0000 0000ff} ${color #22ccff}${upspeedgraph ppp0 22,150 0000ff ff0000}
$color$stippled_hr
$alignc Router Name: ${wireless_essid wlan0}
$color$stippled_hr
${color lightgrey}Wireless:${color #00ee00} wlan0 ${color lightgrey} on $color Internal IP:  ${addr wlan0}
 ${color lightgrey}Down:${color #8844ee} ${downspeed wlan0} k/s${color lightgrey} ${offset 80}Up:${color #22ccff} ${upspeed wlan0} k/s
${color #0000ff}${downspeedgraph wlan0 22,150 ff0000 0000ff} ${color #22ccff}${upspeedgraph wlan0 22,150 0000ff ff0000}
$color$stippled_hr
${color lightgrey}Networking:${color #00ee00} ETH1 ${color lightgrey} on $color ${addr eth1}
${color lightgrey}Link Status:$color ${linkstatus eth1}
 ${color lightgrey}Down:${color #8844ee} ${downspeed eth1} k/s${color lightgrey} ${offset 80}Up:${color #22ccff} ${upspeed eth1} k/s
${color #0000ff}${downspeedgraph eth1 22,150 ff0000 0000ff} ${color #22ccff}${upspeedgraph eth1 22,150 0000ff ff0000}
$color$stippled_hr
${color lightgrey}Networking:
$color PPP0:   downloaded ${totaldown ppp0}; uploaded ${totalup ppp0}
$color WLAN0:  downloaded ${totaldown wlan0}; uploaded ${totalup wlan0}
$color ETH1:   downloaded ${totaldown eth1}; uploaded ${totalup eth1}
$color$stippled_hr
Port Statistics:
${color red} ${tcp_portmon 1 65535 count} $color total connections
                ${color red} ${tcp_portmon 1 1024 count} $color btw ${color red}1-1024
                                ${color green} ${tcp_portmon 80 80 count} $color on ${color red}80
                                ${color green} ${tcp_portmon 20 23 count} $color on ${color red}20-23
                                ${color green} ${tcp_portmon 443 443 count} $color on ${color red}443
```

---

### Post by Smart Viking on 2010-06-19
You must be root to save a file in the "/home" directory, rather save it in the "/home/<username>" directory.

:)

EDIT:

Here is mine ".conkyrc" file, if you replace all the text in yours with mine, it should work again. (but yours will look exactly like mine, you might want to change that.

```
# Conky, a system monitor, based on torsmo
#
# Any original torsmo code is licensed under the BSD license
#
# All code written since the fork of torsmo is licensed under the GPL
#
# Please see COPYING for details
#
# Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
# Copyright (c) 2005-2010 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
# All rights reserved.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

alignment top_right
background no
border_width 1
cpu_avg_samples 2
default_color blue
default_outline_color blue
default_shade_color blue
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
use_xft yes
xftfont DejaVu Sans Mono:size=11
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_type desktop
own_window_transparent yes
own_window_type root
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale yes
show_graph_range no

TEXT
${font Arial:bold:size=15}${color orange} SmartViking
${font Arial:size=11}
${hr 2}
${color red}Uptime:$color $uptime
${color yellow}Frequency (in MHz):$color $freq
${color red}Frequency (in GHz):$color $freq_g
${color yellow}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color red}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color yellow}CPU Usage:$color $cpu% ${cpubar 4}
${color red}Processes:$color $processes  ${color red}Running:$color $running_processes
${hr 2}
${color yellow}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar 6 /}
${color red}Networking:
Up:$color ${upspeed eth0} ${color red} - Down:$color ${downspeed eth0}
${hr 2}
${color yellow}Name              PID   CPU%   MEM%
${color purple} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color purple} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color purple} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color purple} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
```

---

### Post by localguy on 2010-06-19
> **Smart Viking said:**
> You must be root to save a file in the "/home" directory, rather save it in the "/home/<username>" directory.

:)
  ok its works now i was doing it from my desktop, cool thats 1 problem solved now to figure out why my desktop icons dissapear when conky is running? LoL

---

