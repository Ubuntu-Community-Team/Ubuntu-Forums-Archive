---
title: "Conky-- Wireless Problems"
date: 2009-11-01
forum: General Help
---

### Post by meowzers on 2009-11-01
Ok, so this morning I set out to add conky to 9.10.  After install, which included weather and g-mail scripts I ran it and it worked......with some errors.  When I am connected with ethernet cable, I can see the weather / forecast / network.  This being said, it flickers and resizes itself continuously.    On the other hand, when I am connected wirelessly I do not get an weather / forecast / network however I do NOT have flickering or resizing.  my .conkyrc and lfconfig are below.  Help me make this pretty script function completely!


```
# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 140 5
#maximum_width 140

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
#default_shade_color black
#default_outline_color white
own_window_colour white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35
gap_y 50

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
${voffset 2}${font OpenLogos:size=16}u${font}   Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}A${font}   CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
${font StyleBats:size=16}A${font}   CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
${font StyleBats:size=16}g${font}   RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font}   SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font Webdings:size=16}~${font}  Battery: ${battery_percent BAT0}% ${alignr}${battery_bar 8,60 BAT0}
${font StyleBats:size=16}q${font}   Uptime: ${alignr}${uptime}

DATE ${hr 2}
${alignc 35}${font Arial Black:size=26}${time %H:%M}${font}
${alignc}${time %A %d %Y}

HD ${hr 2}
${voffset 4}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Root:
${voffset 4}${fs_used /}/${fs_size /} ${alignr}${fs_bar 8,60 /}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home:
${voffset 4}${fs_free /home}/${fs_size /home} ${alignr}${fs_bar 8,60 /home}

NETWORK ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}Z${font}   Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public Ip: ${alignr}${execi 1 ~/.scripts/ip.sh}
${else}${if_existing /proc/net/route eth0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth0}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public Ip: ${alignr}${execi 1 ~/.scripts/ip.sh}
${endif}${else}${if_existing /proc/net/route eth1}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth1}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth1}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth1}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public Ip: ${alignr}${execi 1 ~/.scripts/ip.sh}
${endif}${else}${if_existing /proc/net/route ppp0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth1}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth1}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth1}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public Ip: ${alignr}${execi 1 ~/.scripts/ip.sh}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Network Unavailable
${endif}
WEATHER ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=USLA0338 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=USLA0338 --datatype=HT}${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=USLA0338 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=USLA0338 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=USLA0338 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=USLA0338 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=USLA0338 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=USLA0338 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USLA0338 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=USLA0338 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USLA0338 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=USLA0338 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USLA0338 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=USLA0338 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USLA0338 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${voffset 0}Wind: ${alignr}${execi 600 conkyForecast --location=USLA0338 --datatype=WS}
${voffset 0}Humidity: ${alignr}${execi 600 conkyForecast --location=USLA0338 --datatype=HM}
${else}${if_existing /proc/net/route eth0}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=USLA0338 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=USLA0338 --datatype=HT}${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=USLA0338 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=USLA0338 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=USLA0338 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=USLA0338 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=USLA0338 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=USLA0338 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USLA0338 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=USLA0338 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USLA0338 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=USLA0338 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USLA0338 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=USLA0338 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USLA0338 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${voffset 0}Wind: ${alignr}${execi 600 conkyForecast --location=USLA0338 --datatype=WS}
${voffset 0}Humidity: ${alignr}${execi 600 conkyForecast --location=USLA0338 --datatype=HM}
${endif}${else}${if_existing /proc/net/route eth1}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=USLA0338 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=USLA0338 --datatype=HT}${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=USLA0338 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=USLA0338 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=USLA0338 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=USLA0338 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=USLA0338 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=USLA0338 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USLA0338 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=USLA0338 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USLA0338 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=USLA0338 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USLA0338 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=USLA0338 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USLA0338 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${voffset 0}Wind: ${alignr}${execi 600 conkyForecast --location=USLA0338 --datatype=WS}
${voffset 0}Humidity: ${alignr}${execi 600 conkyForecast --location=USLA0338 --datatype=HM}
${endif}${else}${if_existing /proc/net/route ppp0}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=USLA0338 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=USLA0338 --datatype=HT}${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=USLA0338 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=USLA0338 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=USLA0338 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=USLA0338 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=USLA0338 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=USLA0338 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USLA0338 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=USLA0338 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USLA0338 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=USLA0338 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USLA0338 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=USLA0338 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USLA0338 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${voffset 0}Wind: ${alignr}${execi 600 conkyForecast --location=USLA0338 --datatype=WS}
${voffset 0}Humidity: ${alignr}${execi 600 conkyForecast --location=USLA0338 --datatype=HM}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Weather Unavailable
${endif}

EMAIL ${hr 2}

${voffset -8}${font Martin Vogel's Symbols:size=19}B${font}  Gmail: ${alignr}${font DejaVu Sans:style=Bold:size=8}${execi 600 conkyEmail --servertype=IMAP --servername=imap.googlemail.com --username=j.mckenney00@gmail.com --password= --ssl}${font} New email(s)


```



```
eth0      Link encap:Ethernet  HWaddr 00:1b:24:47:0d:f5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0x4000 

eth2      Link encap:Ethernet  HWaddr 00:1a:73:5b:94:fc  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fe5b:94fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1301 errors:0 dropped:0 overruns:0 frame:4825
          TX packets:1315 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1198095 (1.1 MB)  TX bytes:254118 (254.1 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)




```

---

### Post by yeleek on 2009-11-02
Your conkyrc is carrying out an if statement against wlan0.  Do you even have a wlan0?    

That file is fairly complex - why not try a basic conkyrc against your wireless adapter until you get use to formatting them - then move onto this.

---

