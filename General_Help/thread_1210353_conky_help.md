---
title: "conky help"
date: 2009-07-11
forum: General Help
---

### Post by rocketflame on 2009-07-11
I installed conky on 9.04 and added the command "conky" to startup applications. but when i turn my computer on, conky comes on, but on top of other windows, and has some kind of border/shadow around it. if i kill it then restart it with the command "conky" again, it works fine.

I have dual monitors and and nvidea card, the 180 driver. any ideas on how to fix it?

---

### Post by rocketflame on 2009-07-11
Bump

---

### Post by nice_like_rice on 2009-07-11
What is your config like? I have it working perfectly on my system, try the steps explained here [http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html](http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html), just at a guess I would say your config file isn't setup correctly. Just see what results you get with the example config posted there.

Maybe it has something to do with the "own_window true" line...

---

### Post by rocketflame on 2009-07-11
I tried the .conkyrc file on the site, same result. here is my file:

```
# set to yes if you want Conky to be forked in the background
background no

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

own_window_transparent yes
#own_window_colour hotpink
# Text alpha when using Xft
xftalpha 0.8

on_bottom yes

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager
own_window_type override

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 260 5
maximum_width 300

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders no

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
#minimum_size 10 10
gap_x 15
gap_y 70
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# none, xmms, bmp, audacious, infopipe (default is none)
xmms_player bmp

TEXT
${color #0077ff}$sysname $kernel $machine - $nodename 

${color #0077ff}Uptime:${color lightgrey} $uptime ${color #0077ff} Load:${color lightgrey} $loadavg

${color #0077ff}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${color lightgrey}${freq_dyn}Mhz
${color #0077ff}Usage:${color #0077ff} ${color lightgrey}${cpu}% ${color #0077ff}${cpubar}
${color #0077ff}${cpugraph 000000 0077ff}
${color #0077ff}Proces:${color lightgrey} $processes  ${color #0077ff}Run:${color lightgrey} $running_processes ${color #0077ff}CPU:${color lightgrey} ${i2c temp 2}C${color lightgrey} ${color #0077ff}MB:${color lightgrey} ${i2c temp 1}C

${color #0077ff}RAM:${color lightgrey} $mem/$memmax - $memperc% ${alignr}${color #0077ff}${membar 5,110}
${color #0077ff}SWP:${color lightgrey} $swap/$swapmax - $swapperc% ${alignr}${color #0077ff}${swapbar 5,110}

${color #0077ff}Hard Disks:
${color #0077ff} Home ${color lightgrey}${fs_used /home}/${fs_size /home}${alignr}${color #0077ff}${fs_bar 5,120 /home}

${color #0077ff}CPU Usage         PID     CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color #0077ff} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color #0077ff} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #0077ff}Mem Usage
${color lightgrey} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color #0077ff} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color #0077ff} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

${color #0077ff}Network: ${color lightgrey}${addr eth0}

${color #0077ff}Down:${color lightgrey} ${downspeed eth0} k/s $alignr${color #0077ff} Up:${color lightgrey} ${upspeed eth0} k/s
${color #0077ff}${downspeedgraph eth0 27,120 000000 0077ff 180} $alignr${color #0077ff}${upspeedgraph eth0 27,120 000000 0077ff 25}
${color lightgrey}${totaldown eth0}           $alignr${color lightgrey}${totalup eth0}

${color #0077ff}Port(s)${alignr}#Connections
${color #0077ff}Inbound: ${color lightgrey}${tcp_portmon 1 32767 count}  ${color #0077ff}Outbound: ${color lightgrey}${tcp_portmon 32768 61000 count}${alignr}${color #0077ff}Total: ${color lightgrey}${tcp_portmon 1 65535 count}

${color #0077ff}Inbound Connection ${alignr} Local Service/Port${color lightgrey}
 ${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
 ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
 ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
 ${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
 ${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}
 ${tcp_portmon 1 32767 rhost 5} ${alignr} ${tcp_portmon 1 32767 lservice 5}
 ${tcp_portmon 1 32767 rhost 6} ${alignr} ${tcp_portmon 1 32767 lservice 6}
```

---

### Post by rocketflame on 2009-07-12
bump

---

### Post by rocketflame on 2009-07-13
bump?

---

### Post by b.a.w on 2009-07-13
You may want to delay when conky starts. I had to do it for my setup. I tried to sleep it from the startup programs in gnome, but that didn't seem to work so I just made a little text file that I ran.

Put
```
sleep 20 && conky
```
in a file probably in your home. I named my .startconky.sh. Make it executable by right clicking on it, Properties, and Permissions tab. Check mark the allowing executing box. Now add this file to your gnome startup programs. Hopefully this solves your problem.

---

### Post by rocketflame on 2009-07-14
@b.a.w.

works great! Thanks a lot :)

---

