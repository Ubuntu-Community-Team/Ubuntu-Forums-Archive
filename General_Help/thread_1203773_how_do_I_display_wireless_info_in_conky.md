---
title: "how do I display wireless info in conky?"
date: 2009-07-03
forum: General Help
---

### Post by zachthejones on 2009-07-03
I have recently discovered Conky and I absolutely love it. The only problem, so far, is I have no idea how to get it to show my wireless activity (upload, download, connection quality/strength, uptime, etc.). Here's what my conky.conf file looks like:

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
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#
# $Id: conky.conf 1193 2008-06-21 20:37:58Z ngarofil $

    background yes
    use_xft yes
    xftfont 123:size=8
    xftalpha 0.1
    update_interval 0.5
    total_run_times 0
    own_window yes
    own_window_type normal
    own_window_transparent yes
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
    double_buffer yes
    minimum_size 250 5
    maximum_width 400
    draw_shades no
    draw_outline no
    draw_borders no
    draw_graph_borders no
    default_color gray
    default_shade_color red
    default_outline_color green
    alignment top_right
    gap_x 10
    gap_y 10
    no_buffers no
    uppercase no
    cpu_avg_samples 2
    net_avg_samples 1
    override_utf8_locale yes
    use_spacer yes
    text_buffer_size 256

    TEXT

    ${font Arial:size=20}${color Tan1}${alignc}Ubuntu${color Ivory}Linu${font openlogos:size=20}x

    ${voffset -90}
    ${color DimGray}
    ${font}
    ${font Arial:bold:size=10}${color Tan1}SYSTEM ${color DarkSlateGray} ${hr 2}
    $font${color DimGray}$sysname $kernel $alignr $machine
    Intel Celeron $alignr${freq_g cpu0}Ghz
    Uptime $alignr${uptime}
    File System $alignr${fs_type}

    ${font Arial:bold:size=10}${color Tan1}PROCESSOR ${color DarkSlateGray}${hr 2}
    $font${color DimGray}CPU  $cpu% ${cpubar 4}

    ${font Arial:bold:size=10}${color Tan1}MEMORY ${color DarkSlateGray}${hr 2}
    $font${color DimGray}MEM $alignc $mem / $memmax $alignr $memperc%
    $membar

    ${font Arial:bold:size=10}${color Tan1}HDD ${color DarkSlateGray}${hr 2}
    $font${color DimGray}HDD $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
    ${fs_bar /}

    ${font Arial:bold:size=10}${color Tan1}TOP PROCESSES ${color DarkSlateGray}${hr 2}
    ${color DimGray}$font${top_mem name 2}${alignr}${top mem 2} %
    $font${top_mem name 3}${alignr}${top mem 3} %
    $font${top_mem name 4}${alignr}${top mem 4} %
    $font${top_mem name 5}${alignr}${top mem 5} %

    ${font Arial:bold:size=10}${color Tan2}NETWORK ${color DarkSlateGray}${hr 2}
    $font${color DimGray}IP on eth0 $alignr ${addr eth0}

    Down $alignr ${downspeed eth0} kb/s
    Up $alignr ${upspeed eth0} kb/s

    Downloaded: $alignr  ${totaldown eth0}
    Uploaded: $alignr  ${totalup eth0}

    ${font Arial:bold:size=10}${color Tan2}TIME ${color DarkSlateGray}${hr 2}

    ${color DarkSlateGray} ${font :size=30}$alignc${time %H:%Mh}
    ${voffset -30}${font :bold:size=10}$alignc${time %d %b. %Y}
    ${font :bold:size=8}$alignc${time %A}
    $endif
```

I've attached a copy of what it looks like on my desktop. Any help would be greatly appreciated!

---

### Post by handaxe on 2009-07-03
```
${if_up eth1}${color e07401}WIRELESS (IP: ${addr eth1}- qual: ${wireless_link_qual_perc eth1}%) ${hr 2}$color
${color A6A6A6}Essid: ${wireless_essid eth1} ${alignr}Rate: ${wireless_bitrate eth1}${color}
${color A6A6A6}Down: ${downspeed eth1} kB/s ${alignr}Up: ${upspeed eth1} kB/s$color
${color A6A6A6}${downspeedgraph eth1 25,140 000000 970300} ${alignr}${upspeedgraph eth1 25,140 000000 297F00}$color
${color A6A6A6}Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}$color$endif
```Does this snippet help?  Alter eth1 etc and colours  as needed, of course.

HA

---

### Post by zachthejones on 2009-07-04
Yeh, that was the help I needed...I finally figured out what my installation called the wireless connection by right clicking on my wireless icon in the sys tray and choosing "Connection Information". My computer detects the wireless as wlan0 - once I changed from eth1 to wlan0 it detected it and displayed the information. I still gotta tweak the look and info from what you gave me - I'll post a pic when I get that done!

---

