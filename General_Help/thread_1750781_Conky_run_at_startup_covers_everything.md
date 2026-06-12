---
title: "Conky run at startup covers everything"
date: 2011-05-05
forum: General Help
---

### Post by alanwalterthomas on 2011-05-05
I want conky to run at startup. I put an entry in startup applications but when it starts it covers everything (see attached image). I can fix it (i.e. moving a window over it covers conky) by running killall conky && conky , but I don't want to have to do that all the time.
I suspect the problem has to do with the window type, but don't know how to fix it. Also, I don't want to lose sight of the icons/files on the desktop.
Here's my conky.rc:

# UBUNTU-CONKY

# Create own window instead of using desktop (required in nautilus)
own_window true
own_window_type override
own_window_hints below

# colorize.sh 
# [http://conkyhardcore.com/beginners/how-did-he-do-that/crinos512/colorizesh/](http://conkyhardcore.com/beginners/how-did-he-do-that/crinos512/colorizesh/)
#colours below used by colorize script
color7 lightblue
color8 yellow
color9 red

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 1.0

#Maximum Width of Window
maximum_width 400

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font georgia:size=10
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 5

# border width
border_width 6

# Default colors and also border colors, grey90 == #e5e5e5
default_color FFFFCC

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after TEXT will be formatted on screen
#
#
#
#
#
#
#
#
#
#
#
#
TEXT
${color FFFFFF}
$alignc ${voffset -6}_______________${voffset 6}ALAN'S COMPUTER${voffset -6}_______________
${color 0000CC}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine $alignr System Updates: $color${execi 3600 aptitude search "~U" | wc -l | tail}
$alignr System Fan $color ${execpi 6 sensors | grep 'fan2' | cut -c13-16 | xargs ~/Documents/Computer/Conky/SystemFancolorize.sh} RPM $color
${color 0000CC}CPU ${hr 2}$color
${cpugraph FFFF00 0000FF}
AMD Phenom(tm) II X4 945 Processor$alignr CPU Temperature: $color ${execpi 6 sensors | grep 'temp2' | cut -c15-16 | xargs ~/Documents/Computer/Conky/TotalCPUcolorize.sh}°C $color
Total CPU: ${cpu cpu0}% $alignr CPU Fan Speed: $color ${execpi 6 sensors | grep 'fan1' | cut -c13-16 | xargs ~/Documents/Computer/Conky/CPUFancolorize.sh} RPM $color
${font georgia:size=8}Core 1: ${freq_g 1} GHz ${tab 20}Core 2: ${freq_g 2} GHz ${tab 20}Core 3: ${freq_g 3} GHz ${tab 20}Core 4: ${freq_g 4} GHz 
${font terminous:size=18}${color 0000FF}
${cpu cpu1}%${color 0000FF}${cpugraph cpu1 20,30 00FF00 FF0000 -t} ${tab 5} ${cpu cpu2}%${color 0000FF}${cpugraph cpu2 20,30 00FF00 FF0000 -t} ${tab 5} ${cpu cpu3}%${color 0000FF}${cpugraph cpu3 20,30 00FF00 FF0000 -t} ${tab 5} ${cpu cpu4}%${color 0000FF}${cpugraph cpu4 20,30 00FF00 FF0000 -t} 
#
#
#
#
#
${color 0000FF}${font monotype:style=bold,size=10}PROCESS NAME ${alignr 85}PID${alignr 43}CPU%$alignr MEM% ${font monotype:size=7}${color CCFFFF}
${top name 1} ${alignr 120} ${top pid 1} ${alignr 70} ${top cpu 1} % ${alignr 7} ${top mem 1} %
${top name 2} ${alignr 120} ${top pid 2} ${alignr 70} ${top cpu 2} % ${alignr 7} ${top mem 2} %
${top name 3} ${alignr 120} ${top pid 3} ${alignr 70} ${top cpu 3} % ${alignr 7} ${top mem 3} %
${top name 4} ${alignr 120} ${top pid 4} ${alignr 70} ${top cpu 4} % ${alignr 7} ${top mem 4} %
${top name 5} ${alignr 120} ${top pid 5} ${alignr 70} ${top cpu 5} % ${alignr 7} ${top mem 5} %$color

$font${color 0000CC}MEMORY ${hr 2}$color
${memgraph 0000FF FFFF00}
#(height),(width) (gradient colour 1) (gradient colour 2) (scale) (-t) (-l)
RAM Used: ${mem} $alignr Available RAM: ${memeasyfree}/${memmax}
RAM: $memperc%  ${color 33FFFF} ${membar 6} $color
Buffers: ${buffers} $alignc Cache ${cached} $alignr ${color CCCC33}$swap Swap used$color
#Free Mem: ${memfree} $alignc Easily Freed Mem: ${memeasyfree}
Swap: $swapperc%   ${color CCCC33} ${swapbar 6} $color

${color 0000CC}GPU - ATI RADEON HD 4670 ${hr 2}$color 
GPU Core Clock $alignr ${execpi 6 aticonfig --odgc | grep Current\ Clocks | cut -c32-35 | xargs ~/Documents/Computer/Conky/GPUCOREcolorize.sh}$color
GPU Memory Clock $alignr ${execpi 6 aticonfig --odgc | grep Current\ Clocks | cut -c45-49 | xargs ~/Documents/Computer/Conky/GPUMEMcolorize.sh}$color
GPU Load $alignr ${execpi 6 aticonfig --odgc | grep load | awk '{print $4}' | tr -d % | xargs ~/Documents/Computer/Conky/GPULOADcolorize.sh}%$color
GPU Temp $alignr ${execpi 6 aticonfig --odgt | grep Sensor | cut -c43-44 | xargs ~/Documents/Computer/Conky/GPUTEMPcolorize.sh}°C

${color 0000CC}STORAGE ${hr 2}$color
System $alignr ${fs_type} ${fs_free_perc /}% free ${color 993300} ${fs_bar 6,180 /}$color
Users $alignr ${fs_type} ${fs_free_perc /home}% free ${color FFFF00} ${fs_bar 6,180 /home}$color${if_mounted /media/CE16645616644217}
Windows 7 $alignr NTFS ${fs_free_perc /media/CE16645616644217}% free ${color 0000FF} ${fs_bar 6,180 /media/CE16645616644217}$color${endif}
Win7Backup ${if_mounted /media/CE16645616644217}$alignr ${fs_type} ${fs_free_perc /media/Win7Backup}% free ${color 006600} ${fs_bar 6,180 /media/Win7Backup}$color${endif}

${color 0000CC}DISK STATUS ${hr 2} $${color 0000FF}${font monotype:style=bold:size=8}
Disk ${tab 15} Temp ${tab 20} Reads ${tab 35} Writes ${tab 90} Total Disk I/O
$color$font  1 ${tab 25} ${execi 60 hddtemp /dev/sda | cut -c34-38} ${tab 25} ${diskio_read /dev/sda} ${tab 45} ${diskio_write /dev/sda} ${tab 25}
  2 ${tab 25} ${execi 60 hddtemp /dev/sdb | cut -c34-38} ${tab 25} ${diskio_read /dev/sdb} ${tab 45} ${diskio_write /dev/sdb} ${tab 25}
${offset 252} ${voffset -37}${diskiograph 30,150 00FF00 FF0000 -t}

#
${color 0000CC}NETWORK ${hr 2}$color
#Local IP: ${addr eth0} $alignr External IP: ${execi 21600 wget -O - [http://whatismyip.org/](http://whatismyip.org/) | tail}
Down: $color${downspeed eth0} ${alignr}Up: ${upspeed eth0}
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0
25,140 000000 00ff00}$color
Total Down: ${totaldown eth0} ${alignr}Total Up: ${totalup eth0}

${color 0000CC}MUSIC ${hr 2}$color $font
Title:                                     Artist:                            Currently ${exec conkyRhythmbox -d ST}$alignr${exec conkyRhythmbox -d PT}
${exec conkyRhythmbox -m 20 -d TI} ${tab 70, 0} ${exec conkyRhythmbox -m 20 -d AR} $alignr of  ${exec conkyRhythmbox -d LE}
$alignr ${offset -90} ${voffset -15} ${font Terminus:style=Bold:size=16} ${exec conkyRhythmbox -d RT} $font
#
#

#
#
${color 0000CC}MAIL: ${font georgia:style=Bold:size=8}$color ${execi 1800 conkyEmail --servertype=IMAP --servername=imap.gmail.com --username=email@gmail.com --password=not_my_password --ssl -i 5}${font}${color 0000CC}

${color 0000CC}UPCOMING EVENTS ${hr 2}$color
${execi 1800 conkyGoogleCalendar -u [email]email@gmail.com[/email] -p not_my_password -a}$font

---

### Post by jeremy1138 on 2011-05-07
Hello.  I'm having this same problem.  I think I remember this happening to me like 3 or 4 years ago but I looked back through my posts and I couldn't find it.  I think the solution involved somehow delaying the start of conky when logging into the desktop.

Can anyone confirm that and let us know how it can be accomplished?

Thanks!

---

### Post by jeremy1138 on 2011-05-07
I found it.  You have to create a script to start conky with a delay and then call that at startup instead of conky directly.  See here:

[http://ubuntuforums.org/showthread.php?t=1539575&highlight=conky+delay](http://ubuntuforums.org/showthread.php?t=1539575&highlight=conky+delay)

---

### Post by Habitual on 2011-05-07
Alan:

Open a terminal and create this shell script, substituting the path to your own conkyrc file.
```
#!/bin/bash
sleep 3
conky -c /path/to/conkyrc &

```

Save it in your ~/Documents as startconky.sh or similar.
Open a terminal or re-use same and type
```
chmod 700 ~/Documents/startconky.sh
```

Now go to startup programming under Preferences and create a new startup item pointing at ~/Documents/startconky.sh

Done.

---

### Post by alanwalterthomas on 2011-05-18
Thanks! Delaying conky at startup did the trick.

---

