---
title: "Conky 1.8 on ubuntu 10.04 problem"
date: 2010-05-02
forum: General Help
---

### Post by vzhen on 2010-05-02
Before this,
I am not sure where to post this topic.

Before i upgraded to ubuntu 10.04. My conky 1.8 running without problems under 9.04


Problem 1: If i kill conky and re-run it with alt + f2. my conky only display with 2x2 pixels square at the right top.

Problem 2: wan-ip not display on ubuntu 10.04. 
No problem in ubuntu 9.04

If i restart my laptop and let it run at startup then no problem

Below is my conkyrc & startup script(.ssc.sh) & .wan-ip.sh
```
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background no

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
xftfont Trebuchet MS:size=8

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
update_interval 0.5

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
own_window_colour black

# If own_window is yes, these window manager hints may be used
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 230 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_inner_margin 4

# border width
border_width 1


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
gap_x 12
gap_y 12

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
use_spacer none

# Shows the maximum value in scaled graphs.
show_graph_scale no

# Shows the time range covered by a graph.
show_graph_range no

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 256

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
#max_user_text 16384

# Timing interval for music player thread, e.g. mpd, audacious
#music_player_interval (update_interval is default)

# Strictness of if_up. One of: up, link or address. The later ones imply the further ones.
# Defaults to up.
#if_up_strictness address

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
${alignc 35}${font Trebuchet MS:size=15}$nodename${font}


SYSTEM ${hr 2}
${color lightgrey}
CPU: $cpu% ${alignr}${cpubar 8,60}
RAM: $mem ${alignr}$memperc% ${membar 8,60}
CPU temp: ${acpitemp}C
Uptime: $uptime 
${color}


DATE ${hr 2}

${alignc 35}${font Trebuchet MS:size=26}${time %H:%M}${font}
${alignc}${color lightgrey}${time %a %d %b %Y}${color}


HDD ${hr 2}

Home: 
${color lightgrey}${fs_used /home} / ${fs_size /home}${alignr}${fs_used_perc /home}% ${fs_bar 8,60 /home}${color}

Root: 
${color lightgrey}${fs_used /root} / ${fs_size /root}${alignr}${fs_used_perc /root}% ${fs_bar 8,60 /root}${color}


NETWORK ${hr 2}
${if_existing /proc/net/route wlan0}
${color lightgrey}Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 789E2D A7CC5C}
Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,60 789E2D A7CC5C}
Upload: ${alignr}${totalup wlan0}
Download: ${alignr}${totaldown wlan0}
Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
Gateway IP: ${alignr}${gw_ip}
Local IP: ${alignr}${addr wlan0}${color}
${color lightgrey}Wan IP:$alignr${execi 600 /home/vzhen/.wan-ip.sh}${color}
${else}${if_existing /proc/net/route eth0}
${color lightgrey}Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,60 789E2D A7CC5C}
Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,60 789E2D A7CC5C}
Upload: ${alignr}${totalup eth0}
Download: ${alignr}${totaldown eth0}
Gateway IP: ${alignr}${gw_ip eth0}
Local IP: ${alignr}${addr eth0}${color}
${color lightgrey}Wan IP:$alignr${execi 600 /home/vzhen/.wan-ip.sh}${color}
${else}${if_existing /proc/net/route eth1}
${color lightgrey}Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60 789E2D A7CC5C}
Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60 789E2D A7CC5C}
Upload: ${alignr}${totalup eth1}
Download: ${alignr}${totaldown eth1}
Gateway IP: ${alignr}${gw_ip}
Local IP: ${alignr}${addr eth1}
${color lightgrey}Wan IP:$alignr${execi 600 /home/vzhen/.wan-ip.sh}${color}
${else}${font PizzaDude Bullets:size=14}4${font}   Network Unavailable${color}
${endif}${endif}${endif}
PROCESSES ${hr 2}

${color}Name${alignr}PID     CPU   MEM
${color #ddaa00} ${top name 1} ${alignr}${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${alignr}${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${alignr}${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${alignr}${top pid 4} ${top cpu 4} ${top mem 4}
${color lightgrey} ${top name 5} ${alignr}${top pid 5} ${top cpu 5} ${top mem 5}
${color lightgrey} ${top name 6} ${alignr}${top pid 6} ${top cpu 6} ${top mem 6}
${color lightgrey} ${top name 7} ${alignr}${top pid 7} ${top cpu 7} ${top mem 7}
${color lightgrey} ${top name 8} ${alignr}${top pid 8} ${top cpu 8} ${top mem 8}

```

```
#!/bin/sh
# click to start, click to stop
 
if pidof conky | grep [0-9] > /dev/null
then
exec killall conky
else
 
sleep 15  # sleep not required for xfce on startup - 30 or more for others
conky ~/Conky/conky/main
 
exit
fi
```


```
#!/bin/sh
wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'
```

---

### Post by EdwardMorris on 2010-05-26
Custom compile conky with ./configure --enable-wlan to get the wireless stuff working...as for the other problems, I have no clue.

---

