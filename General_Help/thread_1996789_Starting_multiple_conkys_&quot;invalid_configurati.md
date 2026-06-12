---
title: "Starting multiple conkys &quot;invalid configuration file&quot;"
date: 2012-06-04
forum: General Help
---

### Post by littleport2003 on 2012-06-04
Hi guys, I'm hoping you can give me a bit of a hand with this. I'm trying to run 2 conky windows on my desktop. I have 1 running fine, but I can't get the second one to work.

I have 2 conky configs saved in */etc/home*, *conkyrc.conf* which is working fine, and *conky_2.conf* which isn't working.

In the same folder I have a simple script that I'm trying to use to start both conkys, *dual_conky.sh*
```
#!/bin/bash

sleep 2 &&
conky -d -c /etc/conky/conkyrc &
sleep 5 &&
conky -d -c /etc/conky/conky_2 &
exit
```

When I try to run *dual_conky.sh* in terminal I get:
```
matt@xw6000:~$ cd /etc/conky
matt@xw6000:/etc/conky$ sh dual_conky.sh
matt@xw6000:/etc/conky$ WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-FA4gyI/pkcs11: No such file or directory
Conky: invalid configuration file '/etc/conky/conkyrc'

Conky: no readable personal or system-wide config file found
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-FA4gyI/pkcs11: No such file or directory
Conky: invalid configuration file '/etc/conky/conky_2'

Conky: no readable personal or system-wide config file found

```

Any help will be greatly appreciated, I've spent the last hour or so googling and changing file names etc. but so far nothings worked :confused:

*conkyrc.conf*:
```
background no
font Sans:size=7
#xftfont Sans:size=10
use_xft yes
xftalpha 0.9
update_interval 1
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 220 5
maximum_width 220
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color DimGray
default_shade_color black
default_outline_color green
alignment top_left
gap_x 8
gap_y 5
no_buffers yes
uppercase no
cpu_avg_samples 3
override_utf8_locale no
uppercase yes # set to yes if you want all text to be in uppercase

TEXT
${color 09abe9}SYSTEM ${hr 1}${color}
#Node name: ${alignr}$nodename 
System name: ${alignr}$sysname
Kernel: ${alignr}$kernel
Machine: ${alignr}$machine
Uptime: $alignr$uptime

${voffset -5}${color 09abe9}CPU ${hr 1}${color}
Processes: ${alignr}$processes ($running_processes running)

CPU1 ${alignr}${cpu cpu1}%
${cpugraph cpu1}
CPU2 ${alignr}${cpu cpu2}%
${cpugraph cpu2}
CPU3 ${alignr}${cpu cpu3}%
${cpugraph cpu3}
CPU4 ${alignr}${cpu cpu4}%
${cpugraph cpu4}

Highest CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

${voffset -5}${color 09abe9}MEMORY ${hr 1}${color}
Ram ${alignr}$mem / $memmax ($memperc%)
${membar 4}
swap ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Highest MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

${voffset -5}${color 09abe9}Filesystem ${hr 1}${color}
HDD Free Space: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}

${voffset -5}${color 09abe9}NETWORK ${hr 1}${color}
WiFi: ${wireless_link_qual wlan0}% 
${alignr}${wireless_link_bar 4,220 wlan0}

IP address: ${alignr}${addr wlan0}
Down ${downspeed wlan0} k/s ${alignr}Up ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,107} ${alignr}${upspeedgraph wlan0 25,107}
Total ${totaldown wlan0} ${alignr}Total ${totalup wlan0}

```

*conky_2.conf*:
```
background no
font Sans:size=7
#xftfont Sans:size=10
use_xft yes
xftalpha 0.9
update_interval 1
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 220 5
maximum_width 220
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color DimGray
default_shade_color black
default_outline_color green
alignment top_right
gap_x 8
gap_y 5
no_buffers yes
uppercase no
cpu_avg_samples 3
override_utf8_locale no
uppercase yes # set to yes if you want all text to be in uppercase

TEXT
${voffset -5}${color 09abe9}WEATHER - Milton Keynes ${hr 1}$color$
Precipitation/obscuartion:${alignr 2}${if_match "${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EGTC weather}"==""}none${else}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EGTC weather}${endif}
#Precipitation: ${alignr}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EGTC weather - }
Temperature: ${alignr}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EGTC temperature}${iconv_start UTF-8 ISO_8859-1}° ${iconv_stop}C
Cloud: ${alignr}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EGTC cloud_cover -}
Wind Speed: ${alignr}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EGTC wind_speed -}k/h
Wind Direction: ${alignr}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EGTC wind_dir -}
Last Update: ${alignr}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EGTC last_update - }

${voffset -5}${color 09abe9}WEATHER - London ${hr 1}$color$
Precipitation/obscuartion:${alignr 2}${if_match "${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EGLC weather}"==""}none${else}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EGLC weather}${endif}
#Precipitation: ${alignr}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EGLC weather - }
Temperature: ${alignr}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EGLC temperature}${iconv_start UTF-8 ISO_8859-1}° ${iconv_stop}C
Cloud: ${alignr}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EGLC cloud_cover -}
Wind Speed: ${alignr}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EGLC wind_speed -}k/h
Wind Direction: ${alignr}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EGLC wind_dir -}
Last Update: ${alignr}${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ EGLC last_update - }

${voffset -5}${color 09abe9}Time ${hr 1}$color$
UK current:$alignr ${tztime Europe/London %H:%M}
Greenwich mean time:$alignr ${tztime Europe/GMT %H:%M}
US, Central:$alignr ${tztime US/Central %H:%M}
Victoria, Australia:$alignr ${tztime Australia/Victoria %H:%M}
```

---

### Post by mcduck on 2012-06-04
Based on the errors, neither file is found.

First, you need to include  the .conf part of the file names in the script. And second, check that the path is correct, I really couldn't tell from your post where exactly you have the configuration files, in /etc/conky or in your home, but the script is now looking for them in the former location...

---

### Post by littleport2003 on 2012-06-04
> **mcduck said:**
> Based on the errors, neither file is found.

First, you need to include  the .conf part of the file names in the script. And second, check that the path is correct, I really couldn't tell from your post where exactly you have the configuration files, in /etc/funky or in your home, but the script is now looking for them in the former location...

Thanks for the quick reply, problem now solved with the simple addition of .conf, and a few extra /'s in the script :lolflag:

---

