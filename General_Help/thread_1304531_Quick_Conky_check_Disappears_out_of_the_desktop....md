---
title: "Quick Conky check? Disappears out of the desktop..."
date: 2009-10-29
forum: General Help
---

### Post by Pott on 2009-10-29
Well I edited the standard Conky file. I wanted to delete some areas I didn't care for, and change its position to the Desktop (so other windows run OVER it, not the other way around)

# Conky, a system monitor, based on torsmo
#
# Any original torsmo code is licensed under the BSD license
#
# All code written since the fork of torsmo is licensed under the GPL
#
# Please see COPYING for details
#
# Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
# Copyright (c) 2005-2007 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
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
# along with this program.  If not, see .
#
# $Id: conky.conf 1193 2008-06-21 20:37:58Z ngarofil $
 
alignment tr
own_window yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_type desktop
own_window_transparent yes
background no
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
font 6x10
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
Double_buffer yes
out_to_console no
stippled_borders 0
update_interval 3.0
uppercase no
use_spacer no
show_graph_scale no
show_graph_range no
total_run_times 0
 
TEXT
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
${color grey}Frequency (in GHz):$color $freq_g
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$hr
${color grey}File systems:
$color${fs_free /}/${fs_size /} ${fs_bar 6 /}
$hr
${color grey}Name                 PID  CPU%  MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}


Something's obviously wrong with my parameters... it disappears whenever I Show the Desktop and then doesn't appear again...


EDIT: DOH
I think I accidentally got rid of total_run_times. I added the line set to 0 and it worked for a bit but it's still down now...

---

### Post by Pott on 2009-11-03
Any ideas...?

Here's my current setting:
Here's my conky settings:
alignment tr
own_window yes
own_window_type desktop
own_window_transparent yes
background yes
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
font 6x10
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
Double_buffer yes
out_to_console no
stippled_borders 0
update_interval 3.0
uppercase no
use_spacer no
show_graph_scale no
show_graph_range no
total_run_times 0

---

