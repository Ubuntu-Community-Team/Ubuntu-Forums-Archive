---
title: "Weird conky behavior"
date: 2012-07-09
forum: General Help
---

### Post by MichaelGld on 2012-07-09
I am running conky 1.90 with Ubuntu 11.10 64-bit. Conky has suddenly started acting up in very strange ways. For a couple of days,  the background behind conky has turned white instead of transparent.  If I did killall and reran conky from the terminal, it regained its transparent state. 

Now, when I log in there is no visible conky. If I run Top I can see that conky is running.  The killall and rerun has no visible effect.  I get no errors when running conky from the terminal.

I have recently upgraded from 11.04 using the Update Manager. I have also created two new startup applications: *compiz --replace* and *fusion-icon*.  Even after removing those, the vanishing conky problem remains. 

What's really weird is that with the Compiz Cube in effect, when rotating the cube, I saw Conky.  It disappears when I stop the cube on any of my four desktops.

.conkyrc

```
alignment top_right
background no
border_width 0
cpu_avg_samples 2
default_color white
default_outline_color black
default_shade_color black
double_buffer yes
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades yes
use_xft yes
# xftfont terminus:size=11
xftfont terminus:size=9.5
gap_x 10
gap_y 50
# maximum_width 320
maximum_width 380
minimum_size 300 100
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_transparent yes
own_window_type override
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no
text_buffer_size 4096
temperature_unit fahrenheit

TEXT 
#${execp ~/conkygraphics.sh}
#${font Terminus:style=bold:size=11}SYSTEM $hr

${voffset -33}${font OpenLogos:size=90}${color2}v${font}${voffset -59}${goto 178}${font UbuntuTitleBold:size=20}${color4}11.10${font} 

#Host: $alignr $nodename
#${font Terminus:size=8}
# ${font Terminus:style=bold:size=11}Time: ${time %k:%M:%S}${alignr}${time %a %b %d, %Y}${font}
${font DejaVu Sans Mono:bold:size=11}Time: ${time %k:%M:%S}${alignr}${time %a %b %d, %Y}${font}

# ${font Terminus:style=bold:size=11}SYSTEM $hr${font}
${font DejaVu Sans Mono:bold:size=11}SYSTEM $hr${font}
Uptime: $uptime 
# Updates: ${alignr}${color1}${execi 360 apt-get search "~U" | wc -l | tail}${color} ${color2}Packages${color}${font}
#Updates Available: ${execi 1200 aptitude search "~U" | wc -l | tail}${font}
Ubuntu Version: ${pre_exec lsb_release -r -s}  Oneiric Ocelot
Conky:${conky_version} for ${conky_build_arch}
$sysname $kernel $machine
Speed ${freq}MHz   Load: ${loadavg}
#UPS Load: ${apcupsd_load}
#UPS Load: ${apcupsd_load 127.0.0.1 3551}
#UPS Model: ${apcupsd_model}
#UPS Status: ${apcupsd_status 127.0.0.1 3551}
#UPS Time Remaining: ${apcupsd_timeleft 127.0.0.1 3551} min.
#UPS Loadgauge: ${apcupsd_loadgauge 27,92}
#UPS Load Graph: ${apcupsd_loadgraph 14,80 CE5C00}
${color light blue}
#${font Terminus:style=bold:size=11}PROCESSORS $hr
${font DejaVu Sans Mono:bold:size=11}PROCESSORS $hr
${font}CPU:$alignr AMD ${exec cat /proc/cpuinfo | grep 'model name' | sort -u | cut -c 18-59}
#$alignl${execi 600 sensors -f |grep 'Core 0' |cut -d+ -f2 |sed 's|^\([0-9]*\.[0-9]\).*|\1|'}F
#$alignr ${execi 600 sensors -f |awk '/Core 0/ {cut=index($3, "F"); print(substr($3, 2, cut - 3))}'}
# ${font Terminus:size=9}CPU TEMP: ${acpitemp}°C
#CPU TEMP: ${execi 8 sensors | grep -A 1 'temp1' | cut -c15-18 | sed '/^$/d'}°C  
#CPU - ${execi 60 sensors | grep -A 0 'temp2' | cut -c 15-21} ºC
#CPU Core 1 Temp: $alignr${execi 600 sensors -f | grep 'Core 0' | awk '{print $3}'}
#CPUtemp: $alignr${execi 60 sensors | grep 'CPU Temperature' | cut -c 22-28} 
#CPUTemp ${execi 8 sensors | grep -A 1 'temp2' | cut -c13-16 | sed '/^$/d'}C
#${offset 5}CPUfan: $alignr${hwmon fan 0} RPM
#${offset 5}MBtemp: $alignr${hwmon temp 2}°F
#${offset 5}CPUtemp: $alignr${hwmon temp 1}°F
${font}CPU1: ${cpu cpu0}% ${cpubar cpu0}
CPU2: ${cpu cpu1}% ${cpubar cpu1}
CPU3: ${cpu cpu2}% ${cpubar cpu2}
CPU4: ${cpu cpu3}% ${cpubar cpu3}
${color pink}
${font DejaVu Sans Mono:bold:size=11}MEMORY $hr
${font}RAM ${alignc}     $mem/$memmax  $alignr $memperc%
${membar}
Swap:  ${alignc} $swap/$swapmax $alignr $swapperc%
${swapbar 6}
${color white} 
${font DejaVu Sans Mono:bold:size=11}GRAPHICS $hr${font}
${font}GPU TEMP: ${nvidia temp }°F${font Terminus:size=7} 
${execp ~/conkygraphics.sh}${font}
${color orange}
${font DejaVu Sans Mono:bold:size=11}DISKS $hr
${font}Root ${font}/ $alignc ${fs_used /}/ ${fs_size /} $alignr ${fs_used_perc /}%
${fs_bar /}
HOME: ${alignc }${fs_free /home} /${fs_size /home} $alignr ${fs_used_perc /home}%
${fs_bar /home}
${diskiograph}
#HDD1: ${execi 10 hddtemp -n -u f /dev/sda}°F ${alignr}HDD2: ${execi 10 hddtemp -n -u f /dev/sdb}°F
#HDD1 Temp: ${execi 5 hddtemp /dev/sda | cut -c 34-38} ${alignr}HDD2 Temp: ${execi 5 hddtemp /dev/sdb | cut -c 24-28}
#HDD1 Temp: ${execi 5 hddtemp /dev/sda | cut -c 24-28} ${alignr}HDD2 Temp: ${execi 5 hddtemp /dev/sdb | cut -c 34-38}
#HDD1 Temp:{hddtemp /dev/sda 127.0.0.1 7634}${alignr}HDD2 Temp:{hddtemp /dev/sdb 127.0.0.1 7634}
#HDD1 Temp:${execi 300 nc localhost 7634 | cut -c34-36}&#7506;C
#HDD1 Temp:${execpi 300 hddtemp /dev/sda | cut -c24-27}
#HDD1 Temp:${execi 10 hddtemp --unit=F /dev/sda | cut -b11-28;}
HDD1 Temp:${execi 10 hddtemp --unit=F /dev/sda | cut -b33-38;}°F${alignr}HDD2 Temp:${execi 10 hddtemp --unit=F /dev/sdb | cut -b24-30;}
${font DejaVu Sans Mono:bold:size=11}DROPBOX $hr${font}
${execi 60 du -c ~/Dropbox | awk  'BEGIN{Size=2.5} /total/ {Used=$1/1048576;printf"Size: %.1f GB",Size;printf " Used: %.1f GB",Used;printf " Free: %.1fGB\n",Size-Used}'}
${execibar 60 $HOME/dropbox.sh}
${color green}
${font DejaVu Sans Mono:bold:size=11}TOP PROCESSES $hr${font}
${top name 1}$alignc${top mem 1}$alignr${top cpu 1}%
${top name 2}$alignc${top mem 2}$alignr${top cpu 2}%
${top name 3}$alignc${top mem 3}$alignr${top cpu 3}%
${top name 4}$alignc${top mem 4}$alignr${top cpu 4}%
${color yellow}
${font DejaVu Sans Mono:bold:size=11}NETWORK $hr${font}

D/L: ${downspeed eth0}/s $alignc ${voffset -8}${downspeedgraph eth0 14,80 CE5C00} $alignr ${voffset -8}${totaldown eth0}
${voffset 4}U/L: ${upspeed eth0}/s $alignc${voffset -2} ${upspeedgraph eth0 14,80 CE5C00}$alignr${voffset -13}${totalup eth0}
##WORKS
#Today:${goto 60}${execi 300 vnstat -d | grep "`date +"%D"`" | awk '{print $2 $3}'}${goto 150} Today:${goto 210}${execi 300 vnstat | grep "`date #+"D"`" | awk '{print $5 $6}'}  
#Week:${goto 60}${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'}${goto 150} Week:${goto 210}${execi 300 vnstat -w | grep "current #week" | awk '{print $6 $7}'} 
#Month:${goto 60}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${goto 150} Month:${goto 210}${execi 300 vnstat -m | grep #"`date +"%b '%y"`" | awk '{print $6 $7}'}

#NEW 3/31/2012

${goto 90}${font DejaVu Sans Mono:bold:size=11}INTERNET USAGE
# ${goto 90}${font Terminus:style=bold:size=12}INTERNET USAGE
${goto 90}${voffset -15}______________
# ${goto 90}${font DejaVu Sans Mono:bold:size=10}Down${goto 170}Up${goto 235}Total
${goto 90}${font Terminus:style=bold:bold:size=9}Down${goto 170}Up${goto 235}Total
${goto 10}${font DejaVu Sans Mono:size=8}Yesterday: ${execi 300 vnstat | grep "yesterday" | awk '{print $2 $3}'}${goto 170}${execi 300 vnstat | grep "yesterday" | awk '{print $5 $6}'}${goto 235}${execi 300 vnstat | grep "yesterday" | awk '{print $8 $9}'}
${goto 10}    Today: ${execi 300 vnstat | grep "today" | awk '{print $2 $3}'}${goto 170}${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}${goto 235}${execi 300 vnstat | grep "today" | awk '{print $8 $9}'}
${goto 10}     Week: ${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'}${goto 170}${execi 300 vnstat -w | grep "current week" | awk '{print $6 $7}'}${goto 235}${execi 300 vnstat -w | grep "current week" | awk '{print $9 $10}'}
${goto 10}    Month: ${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${goto 170}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}${goto 235}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $9 $10}'}${font}

${voffset 4}${font PizzaDudeBullets:size=10}a${font}${offset 5}Private${offset 3}IP${alignr}${addr eth0}
${font PizzaDudeBullets:size=10}a${font}${offset 5}Public${offset 7}IP${alignr}${execi 1800 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}


#$hr
#${execp ~/vnstat-conky-script.py}
#${font Terminus:style=bold:size=11}TIME: ${time %k:%M:%S}${alignr}${time %a/%b/%d}
#${color red}${voffset 6}${font Terminus:style=bold:size=11}WEATHER${offset 8}${voffset -2}${hr 2}${font}
#${voffset 0}${goto 57}${font Weather:size=38}y${font}${voffset -33}${offset 14}${font RadioSpace:size=32}${execi 1800 conkyForecast -d HT -i}#${font RadioSpace:size=18}  ${execi 1800 conkyForecast -d HM -i} Hum.${font}
#${voffset 0}${font Ubuntu:size=24}${alignc}${execi 1800 conkyForecast -d CT}${font}
#${voffset 10}${goto 20}${font ConkyWindNESW:size=41}${execi 1800 conkyForecast -d BS}${font}${voffset -40}${goto 98}${font ConkyWeather:size=45}#${execi 1800 conkyForecast -d WF}${font}${voffset -39}${goto 188}${font MoonPhases:size=32}${execi 1800 conkyForecast -d MF}${font}
#${voffset 6}${goto 28}${font DroidSansFallback:bold:size=8.45}${execpi 1800 conkyForecast -d WS -i| sed -e 's/calm'/'\$\{offset 2}Calm/g' -e 's/#mph'/'\$\{offset 2}mph/g'}${goto 88}Feels like ${execi 1800 conkyForecast -d LT -ui}${execpi 1800 conkyForecast -d MP| sed -e 's/First.*'/'\$#\{goto 182}First Qtr/g' -e 's/Last.*'/'\$\{goto 184}Last Qtr/g' -e 's/New.*'/'\$\{goto 195}New/g' -e 's/Full.*'/'\$\{goto 195}Full/g' -e 's/#Waning.*'/'\$\{goto 187}Waning/g' -e 's/Waxing.*'/'\$\{goto 187}Waxing/g'}${font}
#${voffset 8}${goto 36}${font DroidSans:bold:size=8.55}${execi 1800 conkyForecast -d DW -s 1 -w}${goto 89}${execi 1800 conkyForecast -d DW -s 2 -w}#${goto 143}${execi 1800 conkyForecast -d DW -s 3 -w}${goto 197}${execi 1800 conkyForecast -d DW -s 4 -w}${font}
#${voffset 4}${goto 25}${font ConkyWeather:size=32}${execi 1800 conkyForecast -d WF -s 1 -e 4 -S 1}${font}
#${voffset 0}${goto 25}${font DroidSans:bold:size=8.5}${execi 1800 conkyForecast -d HT -s 1 -ui}${offset 2}/${offset 2}${execi 1800 conkyForecast -#d LT -s 1 -ui}${goto 79}${execi 1800 conkyForecast -d HT -s 2 -ui}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 2 -ui}${goto 133}#${execi 1800 conkyForecast -d HT -s 3 -ui}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 3 -ui}${goto 187}${execi 1800 conkyForecast -d #HT -s 4 -ui}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 4 -ui}${font}
#${voffset 0}${font DroidSansFallback:bold:size=8}${alignc 2}Sunrise${offset 1}${execi 1800 conkyForecast --location=USAZ0166 --datatype=SR --#startday=1}${offset 2}|${offset 2}Sunset${offset 1}${execi 1800 conkyForecast --location=USAZ0166 --datatype=SS --startday=1}${font}
##Internet Traffic --NOT WORKING
#Today:${goto 60}${execi 300 vnstat -i eth0 | grep "today" | awk '{print $2 $3}'}${goto 150} Today:${goto 210}${execi 300 vnstat -i #eth0 | grep "today" | awk '{print $5 $6}'}  
#Week:${goto 60}${execi 300 vnstat -i eth0 -w | grep "current week" | awk '{print $3 $4}'}${goto 150} Week:${goto 210}${execi 300 #vnstat -i eth0 -w | grep "current week" | awk '{print $6 $7}'} 
#Month:${goto 60}${execi 300 vnstat -i eth0 -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${goto 150} Month:${goto 210}
#${execi #300 vnstat -i eth0 -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}


```conkygraphics.sh
```

#!/bin/sh
# conkygraphics.sh
# by Crinos512
# Usage:
#  ${execp ~/.conky/conkyparts/conkygraphics.sh}
#
Card=`lspci | grep VGA | tail -c+36 | head -n1`
Driver="NVidia "`nvidia-settings -q NvidiaDriverVersion -t`
Resolution=`nvidia-settings -q FrontEndResolution -t`
Refresh=`nvidia-settings -q RefreshRate3 -t`
Mem=`nvidia-settings -q VideoRam -t`
Clock=`nvidia-settings -q GPU2DClockFreqs -t`
XRandr=`nvidia-settings -q XRandRVersion -t`
OpenGL=`nvidia-settings -q OpenGLVersion -t | head -c6`
Xorg=`cat /var/log/Xorg.0.log | grep "X.Org X Server " | tail -c+16`

# echo "\${color1}\${stippled_hr 1}\${color}"
# echo "\${voffset -6}  Graphics:"
# echo "\${voffset -6}\${color1}\${stippled_hr 1}\${color}"
echo "    \${color2}$Card\${color}\${alignr} @ \${color2}$Clock Mhz\${color}   "
echo "      X.org: \${color2}$Xorg\${color}\${goto 180}Xrandr: \${color2}$XRandr\${color}\${alignr}OpenGL: \${color2}$OpenGL\${color}   "
echo "      Driver: \${color2}$Driver\${color}\${alignr}Screen: \${color2}$Resolution\${color} @ \${color2}$Refresh\${color}   "

exit 0
```Here's a screencap of my cube with conky visible on the right.

Any help would be appreciated.

---

### Post by dino99 on 2012-07-09
a thread about conky settings

[http://ubuntuforums.org/showthread.php?t=1771033](http://ubuntuforums.org/showthread.php?t=1771033)

---

### Post by MichaelGld on 2012-07-09
It turns out that this was a nVidia  video driver issue, not a Conky issue. I went to Additional Drivers and selected the most recent one (version-current-updates), downloaded, installed and rebooted.  Problem solved.

---

