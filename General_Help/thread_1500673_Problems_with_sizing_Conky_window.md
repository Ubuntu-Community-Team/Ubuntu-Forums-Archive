---
title: "Problems with sizing Conky window"
date: 2010-06-03
forum: General Help
---

### Post by brivy on 2010-06-03
I am having a small problem with Conky.  There is a blank space at the bottom of the Conky window that covers part of the dock. I want to eliminate that blank space. I've been through gone through all the documentation and but there is something that I'm missing.  This is my .conkyrc script. Help please!

# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat connections to your computer
#
# Modified from the original Pengo script
#

background yes


# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering
double_buffer yes

# fiddle with window
use_xft yes
xftfont verdana:size=8

# Update interval in seconds
update_interval 2.0

# Minimum size of text area
minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
#font verdana #will comment out because doesn't work
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
# border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color 333333

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 20
gap_y 0

# stuff after ‘TEXT’ will be formatted on screen

TEXT
$color
${color 330000}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

Conky Architecture $conky_build_arch
Conky Build $conky_build_date
Conky Version $conky_version

${color 330000}CPU ${hr 2}$color
${freq}MHz Load: ${loadavg} Temp: ${acpitemp}
$cpubar
${cpugraph CC0033 ffff00}
NAME PID CPU% MEM%
${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

${color 330000}MEMORY / DISK ${hr 2}$color
RAM: $memperc% ${membar 6}$color
Free Mem: $memfree ${membar 6}$color
Free Mem-Easy: $memeasyfree ${membar 6}$color
${color 330000}${hr 2}$color
Swap: $swapperc% ${swapbar 6}$color
Root: ${fs_free_perc /}% ${fs_bar 6 /}$color
Sda1 (NTFS): ${fs_free_perc /media/sda1}% ${fs_bar 6 /media/sda1}$color
#hdb3: ${fs_free_perc /media/hdb3}% ${fs_bar 6 /media/hdb3}

${color 333300}NETWORK Wireless(${addr eth1}) ${hr 2}$color
Down: $color${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s
${downspeedgraph eth1 25,140 000000 ff0000} ${alignr}${upspeedgraph eth1
25,140 000000 00ff00}$color
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

Wireless Bit Rate: ${Wireless_bitrate eth1}
Current Essid: ${wireless_essid eth1}
Connection Quality: ${wireless_link_qual eth1}

${color 330000}NETWORK Ethernet(${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

---

### Post by bra|10n on 2010-06-04
Hi brivy,
Firstly when posting code try to use the code tags[SIZE=4]** #**[/SIZE]
```
paste code here...
```If you don't mind losing the conky shadow, change this line in your conkyrc;
From own_window_type [COLOR=Red]normal[/COLOR]
to
own_window_type [COLOR=Red]override
[COLOR=Black]I noticed you have [/COLOR][/COLOR][COLOR=Navy]own_window_transparent yes[/COLOR] listed twice.
HTH
[COLOR=Red]
[/COLOR]

---

### Post by stinkeye on 2010-06-04
Make sure there is no blank space at the bottom of your conky config.
You shouldn't be able to scroll down past the last line in your config.
Use backspace to get rid of the blank area.

---

### Post by brivy on 2010-06-05
Thank you. That was exactly what I looking for. I had actually had wanted to get rid of the shadow also but I didn't want to ask too much.:)

---

