---
title: "Conky 1.8.0-1 Ubuntu 64bit"
date: 2010-06-07
forum: General Help
---

### Post by gvhools on 2010-06-07
Hello from grecce...

I use Ubuntu 64bit,with gnome 2.30.0
I have a problem with conky,i cant see weather and music in conky.

the code for conky is:

```
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

${font openlogos:size=20}Gio_${font Arial:size=20}${color Tan1}GNU${color Ivory}LINUX${font openlogos:size=20}t

${voffset -90}
${color DimGray}
${font}
${font Arial:bold:size=10}${color Tan1}SYSTEM ${color DarkSlateGray} ${hr 2}
$font${color DimGray}$sysname $kernel $alignr $machine
Intel Pentium D $alignr${freq_g cpu0}Ghz
Uptime $alignr${uptime}
File System $alignr${fs_type}

${font Arial:bold:size=10}${color Tan1}PROCESSORS ${color DarkSlateGray}${hr 2}
$font${color DimGray}CPU1 ${cpu cpu1}% ${cpubar cpu1}
CPU2 ${cpu cpu2}% ${cpubar cpu2}

$nodename $sysname $kernel on $machine
CPU: ${freq}MHz Uptime: ${uptime} 
CPU: $cpu% $cpubar
${cpugraph 000000 FFFFFF}

${font Arial:bold:size=10}${color Tan1}MEMORY ${color DarkSlateGray}${hr 2}
$font${color DimGray}MEM $alignc $mem / $memmax $alignr $memperc%
$membar

Swap ($swapmax): $swapperc% ${swapbar 6}$color

${font Arial:bold:size=10}${color Tan1}HDD ${color DarkSlateGray}${hr 2}
$font${color DimGray}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}
/disk $alignc ${fs_used /media/disk} / ${fs_size /media/disk} $alignr ${fs_free_perc /media/disk}%
${fs_bar /media/disk}
/disk-1 $alignc ${fs_used /media/disk-1} / ${fs_size /media/disk-1} $alignr ${fs_free_perc /media/disk-1}%
${fs_bar /media/disk-1}

${font Arial:bold:size=10}${color Tan1}TOP PROCESSES ${color DarkSlateGray}${hr 2}
${color DimGray}$font${top_mem name 2}${alignr}${top mem 2} %
$font${top_mem name 3}${alignr}${top mem 3} %
$font${top_mem name 4}${alignr}${top mem 4} %
$font${top_mem name 5}${alignr}${top mem 5} %

${font Arial:bold:size=10}${color Tan2}NETWORK ${color DarkSlateGray}${hr 2}
$font${color DimGray}IP on eth0 $alignr ${addr eth0}

Down $alignr ${downspeed eth0} kb/s
Up $alignr ${upspeed eth0} kb/s

Internet Status (${addr eth0}):
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 FFFFFF} ${alignr}${upspeedgraph eth0 25,140 000000 FFFFFF}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

Downloaded: $alignr ${totaldown eth0}
Uploaded: $alignr ${totalup eth0}

${font Arial:bold:size=10}${color Tan2}WEATHER ${color DarkSlateGray}${hr 2}
${font}${color DimGray}

${voffset -25}${font Weather:size=45}${execi 1800 conkyForecast &#8211;location=GRXX0004 &#8211;datatype=GR}
${alignc 22}${voffset -60}${font Arial:bold:size=10}${color DimGray}${execi 1800 conkyForecast &#8211;location=GRXX0004 &#8211;datatype=HT}
$font${voffset -55}${alignr}${color DimGray}Wind: ${execi 1800 conkyForecast &#8211;location=GRXX0004 &#8211;datatype=WS}
${alignr}${color DimGray}Humidity: ${execi 1800 conkyForecast &#8211;location=GRXX0004 &#8211;datatype=HM}
${alignr}${color DimGray}Precipitation: ${execi 1800 conkyForecast &#8211;location=GRXX0004 &#8211;datatype=PC}

${color DimGray}Sunrise: $alignr${execi 1800 conkyForecast &#8211;location=GRXX0004 &#8211;datatype=SR}${alignr}
Sunset: $alignr${execi 1800 conkyForecast &#8211;location=GRXX0004 &#8211;datatype=SS}$color

${font Arial:bold:size=10}${color Tan2}MUSIC ${color DarkSlateGray}${hr 2}
${color DimGray}$font${if_running mpd}
$mpd_smart
$mpd_album
Bitrate $mpd_bitrate kbits/s
$mpd_status $mpd_elapsed/$mpd_length

${font Arial:bold:size=10}${color Tan2}TIME ${color DarkSlateGray}${hr 2}

${color DarkSlateGray} ${font :size=30}$alignc${time %H:%Mh}
${voffset -30}${font :bold:size=10}$alignc${time %d %b. %Y}
${font :bold:size=8}$alignc${time %A}
$endif
```

my PrtScn: [http://i49.tinypic.com/35bw2er.jpg]("http://i49.tinypic.com/35bw2er.jpg")

you have any idea to help me???

If the Thread is rong please moved.Thank you

*Sorry for my bad english*

---

### Post by stinkeye on 2010-06-09
Have you installed conkyForecast and are you using mpd or rhythmbox to play music.
Guide here: [**_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?p=6097476[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=6097476")

---

