---
title: "Conky transparency works on one computer but not on another. Broke after Karmi upgrd"
date: 2009-11-27
forum: General Help
---

### Post by InkyDinky on 2009-11-27
I have a .conkyrc script which I'm having problems getting the transparency to work properly.  It doesn't appear to be the actual script as the transparency works on one computer but not on another.

The script worked on both before the upgrade to Karmic.
FYI, I'm not using compiz.

I have this on the computer that *doesn't* work.:
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)

I have this on the one that *does* work:
01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G400/G450 (rev 82)

here is the .conkyrc```
	use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no

#to get the degree symbol to show up correctly
override_utf8_locale yes

text_buffer_size 6100 # large buffer needed
#max_specials 512 #otherwise ran out of buffer when this was set.
max_user_text 5000

default_color grey
color1 orange
color7 lightblue
color8 yellow
color9 red



##################################################
#instructions:
#double check that you are using the correct ip.  check this using 'ifconfig'
#make sure the path to the directory for the scripts is correct.  You had that one screwed that up for the longest time.
#if you can't access hddtemp via the 'netcat local 7634' command then you can grant access via 'sudo chmod u+s /usr/sbin/hddtemp' or just start the daemon "hddtemp -d /dev/sda1"
#comments can't be placed in the TEXT section.  The commands after the TEXT command are all interpreted and written to the screen.
# the layout also follows the spacing of the calling text. 
TEXT
  ${goto 80}${color 6694B2}${font OpenLogos:size=45} tuvx
  ${voffset -10}${alignc}${color 6694B2}${font OpenLogos:size=45} PRTW
  ${alignc}${color 6694B2}${font Radio Space:size=10}${voffset -35} ${alignc} ${sysname} ${machine} ${kernel}  ${pre_exec cat /etc/issue.net} 
  ${alignc}Gnome ${pre_exec gnome-about --gnome-version | head -n 1 | awk '{print $2}'}
  ${alignc}${color 6694B2}${font Radio Space:size=10} ${alignc} ${nodename} ${nameserver} 
  ${alignc}${color 6694B2}${font Radio Space:size=10} ${alignc}Load Average: ${loadavg}
   ${font weather:size=28}x ${font}HDD: ${execi 60 ~/conkyscripts/hddmonit.sh} °C 
   ${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth0} Kb/s 
   ${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth0} Kb/s 
   ${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth0}
   ${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth0}
   ${offset 4}${alignc}local ip: ${addr eth0}
   ${offset 4}${alignc}external ip: ${execi 6000 wget -O - http://ip.tupeux.com | tail}
   ${color #CCCCCC}Network Connections:$color ${tcp_portmon 1 65535 count}
   ${color BADCDD}Inbound Ports: ${tcp_portmon 1 32767 count}  Outbound Ports: ${tcp_portmon 32768 61000 count}
   ${color #CCCCCC}Outbound Connection ${alignc} Remote Service/Port${color #ffccaa}
   ${tcp_portmon 32768 61000 rhost 0} ${alignc} ${tcp_portmon 32768 61000 rservice 0}
   ${tcp_portmon 32768 61000 rhost 1} ${alignc} ${tcp_portmon 32768 61000 rservice 1}
   ${tcp_portmon 32768 61000 rhost 2} ${alignc} ${tcp_portmon 32768 61000 rservice 2}
   ${color #CCCCCC}Inbound Connection ${alignc} Local Service/Port${color #ffccaa}
   ${tcp_portmon 1 32767 rhost 0} ${alignc} ${tcp_portmon 1 32767 lservice 0}
   ${tcp_portmon 1 32767 rhost 1} ${alignc} ${tcp_portmon 1 32767 lservice 1}
   ${tcp_portmon 1 32767 rhost 2} ${alignc} ${tcp_portmon 1 32767 lservice 2}
   ${color #888888}/dev/sda1    Free:${execi 600 df -h | grep sda1 | cut -c35-39 } ${alignc}${color #888888} Used:${fs_size /} ${fs_used_perc /}% ${alignr}${fs_bar 6,100 /}
   ${color 888888}${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
   ${font DejaVu Sans:size=8}${color #ffccaa}PROCESSES
   ${color #888888}CPU usage   ${alignc}PID	CPU%	MEM%     
   ${color #CCCCCC}${top name 1} ${alignc}${top pid 1}	${top cpu 1}	${top mem 1}  
   ${color #CCCCCC}${top name 2} ${alignc}${top pid 2}	${top cpu 2}	${top mem 2}  
   ${color #CCCCCC}${top name 3} ${alignc}${top pid 3}	${top cpu 3}	${top mem 3}  
   ${color #888888}RAM usage   ${alignc}PID	CPU%	MEM%     
   ${color #CCCCCC}${top_mem name 1} ${alignc}${top_mem pid 1}	${top_mem cpu 1}	${top_mem mem 1}  
   ${color #CCCCCC}${top_mem name 2} ${alignc}${top_mem pid 2}	${top_mem cpu 2}	${top_mem mem 2}  
   ${color #CCCCCC}${top_mem name 3} ${alignc}${top_mem pid 3}	${top_mem cpu 3}	${top_mem mem 3}  
   ${color C2E078}${font PizzaDude Bullets:size=16}J${font} $mem / $memmax
   ${color #ffccaa}${font PizzaDude Bullets:size=16}K${font} $swap / $swapmax 
   ${color #ffccaa}Disk I/O:${alignr}${diskio_read}${offset 3}${diskio_write}
   ${font StyleBats:size=18}P${font}  Work:  ${uptime_short}
${goto 100}${font Radio Space:size=14}${time %A %B %d, %Y}
${goto 120}${font Radio Space:size=42}${time %H:%M}
${voffset -45}${font Radio Space:size=10} ${execi 1000 cat /proc/cpuinfo | grep "model name" | cut -c14-36} ${execi 30 sensors | grep CPU |  cut -c1-20}
${alignc}${execi 60 du -sh ~/.local/share/Trash/files/ | awk '{print $1}' | sed '/^4.0K/ d' | sed 's/$/ in the TRASH /'}
${execpi 1800 conkyForecast --location=USIN0707 --template=/home/nicolae/.conkyforecast.template}
```

I installed xcompmgr but that didn't solve anything.


Any thoughts or ideas as to what to do?  I've tried reading the forums but people's transparency don't seem to be related to mine.

---

### Post by InkyDinky on 2009-12-15
I changed the background and all of the sudden it picked up the background image and transparency was working fine. Go figure.

---

