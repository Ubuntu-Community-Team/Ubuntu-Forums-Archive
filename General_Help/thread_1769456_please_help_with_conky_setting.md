---
title: "please help with conky setting"
date: 2011-05-28
forum: General Help
---

### Post by skumara on 2011-05-28
Hi I'm new and I have problem settign this wonderful conky.My screenshot is attached.

1. How to get the network function to work?
2. how to make the local IP and Public IP to show up?
3. How to set the temperature to work also?

I'm using ubuntu 10.04 LTS.

when I run conky from terminal I get this message:

Conky: /home/kumarasingam/.conkytheme/conkyrc: 22: no such configuration: 'border_margin'
Conky: /home/kumarasingam/.conkytheme/conkyrc: 41: config file error
Conky: desktop window (1c00030) is subwindow of root window (a6)
Conky: window type - override
Conky: drawing to created window (0x2800001)
Conky: drawing to double buffer
sh: /home/kumarasingam/.scripts/ip.sh: not found


my conkyrc file:

```
# Locale, fonts and font sizes.
use_xft yes
xftfont Droid Sans:size=9
override_utf8_locale yes

# Conky performance
update_interval 1
total_run_times 0
double_buffer yes
no_buffers yes
net_avg_samples 2
text_buffer_size 1024

# Execute it in its own window
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Borders, margins.
draw_borders no
border_margin 1

# Own window color
own_window_colour 393834

# Font colors
default_color B7B2AD
#default_color EFEEED

# Text shadows
draw_shades no

# Header colors
color0 DD3A21

# Minimum dimensions
minimum_size 1440 0

# Conky positioning.
alignment bottom_centre
gap_x 30
gap_y 35

# Output
TEXT
${image ~/.conkytheme/pix/frame.png -p 0,0 -s 1280x180}
${voffset 20}${font Droid Sans:style=Bold:size=12}${color0}${goto 256}Disks:${goto 512}Network:${goto 768}Temperatures:${goto 1024}Time and Date:${font}${color}
${voffset 6}${goto 256}System (/):${goto 380}${fs_used /} / ${fs_size /}${goto 512}Upspeed: ${goto 612}${upspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Droid Sans:style=Bold:size=9}  ${upspeed eth0}${font}${goto 768}CPU: ${goto 868}${execi 4 sensors | grep -A 0 'temp2' | cut -c15-18} ºC${goto 1024}${time %H:%M}  ${time %d/%m/%Y}
${goto 15}Kernel: ${goto 100}${kernel}${goto 380}${fs_bar 10,100 /}${goto 512}Downspeed: ${goto 612}${downspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Droid Sans:style=Bold:size=9}  ${downspeed eth0}${font}${goto 768}Hard Disk: ${goto 868}${execi 4 sensors | grep -A 0 'temp1' | cut -c15-18} ºC${goto 1024}${time %A}, ${time %d} ${time %B} ${time %Y}
${goto 15}CPU: ${goto 100}${cpubar cpu1 10,100}${font Droid Sans:style=Bold:size=9}  ${cpu cpu1}%${font}${goto 256}Home (/Home):${goto 380}${fs_free /home} / ${fs_size /home}${goto 512}Total Uploaded: ${goto 612}${totalup eth0}
${goto 15}RAM: ${goto 100}${membar 10,100}${font Droid Sans:style=Bold:size=9}  $memperc%${font}${goto 380}${fs_bar 10,100 /home}${goto 512}Total Download: ${goto 612}${totaldown eth0}
${goto 15}SWAP:${goto 100}${swapbar 10,100}${font Droid Sans:style=Bold:size=9}  $swapperc%${font}${goto 512}Local IP: ${goto 612}${addr eth0}
${goto 15}Uptime: ${goto 100}${uptime}${goto 512}Public IP: ${goto 612}${execi 10800 ~/.scripts/ip.sh}

```

---

### Post by debd on 2011-05-28
Are you sure your network interface is eth0?
you can run ```
ifconfig
``` in a terminal window while the network is up, to know the interface id. it can be eth0, eth1 ..etc if you use a wired connection or it can be it can be wlan0, wlan1 if you use a wireless connection..etc.
Once you know it, replace all the 'eth0' in the conky script with the working interface id. (use 'seach and replace in gEdit)
To add the Public Ip info, replace 
> ```
Public IP: ${goto 612}${execi 10800 ~/.scripts/ip.sh}
``` with this:
```
Public IP: ${goto 612} ${execi 900 wget -q -O - checkip.dyndns.org | cut -d : -f 2 | cut -d "<" -f 1 | cut -d " " -f 2}
```

---

### Post by skumara on 2011-05-28
Thanks I have solved my problems my final configuratio is 

```
# Locale, fonts and font sizes.
use_xft yes
xftfont Droid Sans:size=9
override_utf8_locale yes

# Conky performance
update_interval 1
total_run_times 0
double_buffer yes
no_buffers yes
net_avg_samples 2
text_buffer_size 1024

# Execute it in its own window
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Borders, margins.
draw_borders no
border_margin 1

# Own window color
own_window_colour 393834

# Font colors
default_color B7B2AD
#default_color EFEEED

# Text shadows
draw_shades no

# Header colors
color0 DD3A21

# Minimum dimensions
minimum_size 1440 0

# Conky positioning.
alignment top_left
gap_x 45
gap_y 550

# Output
TEXT
${image ~/.conkytheme/pix/frame.png -p 0,0 -s 1280x180}
${voffset 20}${font Droid Sans:style=Bold:size=12}${color0}${goto 256}Disks:${goto 512}Network:${goto 768}Temperatures:${goto 1024}Time and Date:${font}${color}
${voffset 6}${goto 256}System (/):${goto 380}${fs_used /} / ${fs_size /}${goto 512}Upspeed: ${goto 612}${upspeedgraph wlan0 10,100 B7B2AD B7B2AD}${font Droid Sans:style=Bold:size=9}  ${upspeed wlan0}${font}${goto 768}CPU: ${goto 868}${execi 4 sensors | grep -A 0 'temp1' | cut -c15-18} ºC${goto 1024}${time %H:%M}  ${time %d/%m/%Y}
${goto 15}Kernel: ${goto 100}${kernel}${goto 380}${fs_bar 10,100 /}${goto 512}Downspeed: ${goto 612}${downspeedgraph wlan0 10,100 B7B2AD B7B2AD}${font Droid Sans:style=Bold:size=9}  ${downspeed wlan0}${font}${goto 768}Hard Disk: ${goto 868}${execi 4 sensors | grep -A 0 'temp1' | cut -c15-18} ºC${goto 1024}${time %A}, ${time %d} ${time %B} ${time %Y}
${goto 15}CPU: ${goto 100}${cpubar cpu1 10,100}${font Droid Sans:style=Bold:size=9}  ${cpu cpu1}%${font}${goto 256}Home (/Home):${goto 380}${fs_free /home} / ${fs_size /home}${goto 512}Total Uploaded: ${goto 612}${totalup wlan0}
${goto 15}RAM: ${goto 100}${membar 10,100}${font Droid Sans:style=Bold:size=9}  $memperc%${font}${goto 380}${fs_bar 10,100 /home}${goto 512}Total Download: ${goto 612}${totaldown wlan0}
${goto 15}SWAP:${goto 100}${swapbar 10,100}${font Droid Sans:style=Bold:size=9}  $swapperc%${font}${goto 512}Local IP: ${goto 612}${addr wlan0}
${goto 15}Uptime: ${goto 100}${uptime}${goto 512}Public IP: ${goto 612} ${execi 900 wget -q -O - checkip.dyndns.org | cut -d : -f 2 | cut -d "<" -f 1 | cut -d " " -f 2}

```

---

