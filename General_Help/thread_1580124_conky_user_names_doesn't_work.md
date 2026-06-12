---
title: "conky user_names doesn't work"
date: 2010-09-22
forum: General Help
---

### Post by dln9 on 2010-09-22
I don't understand why in Conky when I use the user_names variable to show the users logged in, it shows nothing.

---

### Post by Toz on 2010-09-22
It works for me (though the output is not pretty). What version of conky are you using and can you show the code you are using to display the info?
/ToZ

---

### Post by dln9 on 2010-09-22
Version 1.8.0.  (I installed the conky-all package via Synaptic.)  

Here is my ~/.conkyrc file contents, the user_names item is in the third line in the "TEXT" category:  

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
default_color white
default_outline_color white
default_shade_color white
double_buffer yes
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
use_xft yes
xftfont DejaVu Sans Mono:size=12
gap_x 15
gap_y 5
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
own_window_type normal
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no

TEXT
#${scroll 16 $nodename - $sysname $kernel on $machine | }
${color white}$nodename  $sysname $kernel on $machine
${color white}Users:  $user_names
${color white}Currently Displayed Desktop:  No. $desktop
$hr
${color white}Uptime:$color $uptime
#${color white}Frequency (in MHz):$color $freq
${color white}Frequency (in GHz):$color $freq_g
${color white}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color white}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color white}CPU Usage:$color $cpu% ${cpubar 4}
${color white}Processes:$color $processes ${color white}Running:$color $running_processes ${color white}| Threads:$color $threads ${color white}Running:$color $running_threads
${color white}Load:$color ${loadavg}
$hr
${color white}File systems:
 /home $color${fs_used /home}/${fs_size /home} ${fs_bar 6 /home}
 /usr  $color${fs_used /usr}/${fs_size /usr} ${fs_bar 6 /usr}
 /var  $color${fs_used /var}/${fs_size /var} ${fs_bar 6 /var}
 /opt  $color${fs_used /opt}/${fs_size /opt} ${fs_bar 6 /opt}
 /     $color${fs_used /}/${fs_size /} ${fs_bar 6 /}
$hr
${color white}Networking:  Up:$color ${upspeed eth1} ${color white}Down:$color ${downspeed eth1}
$hr
${color white}Battery Charge %: $battery_percent%  $battery_bar
$hr
${color white}Time:  ${time %I:%M:%S %p %Z}${color white}  Date:  ${time %A, %m/%d/%Y}

${color white}${exec cal -3}
#${color grey}Name              PID   CPU%   MEM%
#${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
#${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
#${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
#${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

---

### Post by Toz on 2010-09-22
You're code works for me.
See attachment
/ToZ

---

