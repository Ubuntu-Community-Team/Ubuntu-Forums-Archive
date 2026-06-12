---
title: "Conky on 9.10"
date: 2010-01-31
forum: General Help
---

### Post by Burky on 2010-01-31
I have Ubuntu 9.10 (Kernel: 2.6.31-17-generic-pae | i686) with the newest version of Conky installed. I tried pasting the following code in the .conkyrc. 

```
${alignr}${voffset -20}${offset -126}${font Segoe UI:style=Bold:size=44}${time %H:%M}${font}
${font AvantGarde LT Medium:pixelsize=9}${alignr}${voffset 3}${time %A %d %B %Y}
${voffset 3}${alignr}${if_mpd_playing}${mpd_title} - ${mpd_artist}${endif}
${voffset 3}${alignr}RAM: ${mem}
${voffset 3}${alignr}CPU: ${cpu cpu0}%
${voffset 3}${alignr}${execpi 300 python ~/.scripts/gmail_parser.py user pass 3}${font}
```

I was hoping it would look like this ([click here to see]("http://imgur.com/5q2d1.png")). But instead it won't auto-start and when I run conky -a top_right in a terminal, I get this:

```
david@david-desktop:~$ conky -a top_right
Conky: /home/david/.conkyrc: 1: no such configuration: '${alignr}${voffset'
Conky: /home/david/.conkyrc: 2: no such configuration: '${font'
Conky: /home/david/.conkyrc: 3: no such configuration: '${voffset'
Conky: /home/david/.conkyrc: 4: no such configuration: '${voffset'
Conky: /home/david/.conkyrc: 5: no such configuration: '${voffset'
Conky: /home/david/.conkyrc: 6: no such configuration: '${voffset'
Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
	This program is calling the Imlib call:

	imlib_context_free();

	With the parameter:

	context

	being NULL. Please fix your program.

```

This is my first time ever using Conky, so to tell you the honest truth I have no idea what I'm doing. Anyone think they can help me?

---

### Post by Brandon Williams on 2010-01-31
Your conkyrc file should have a line that says 'TEXT' to indicate that the configuration part of the file is complete and the rest of the content describes the output. Add such a line as the very first one in the file.

This probably won't be quite what you want yet. You're likely to need to add some configuration settings before the 'TEXT' line in order to get the format how you want it.

---

### Post by Burky on 2010-01-31
After I got this.

```
david@david-desktop:~$ conky -a top_right
Conky: desktop window (18000a7) is subwindow of root window (13c)
Conky: drawing to desktop window
Conky: drawing to single buffer
Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

python: can't open file '/home/david/.scripts/gmail_parser.py': [Errno 2] No such file or directory
Conky: can't load font 'Segoe UI:style=Bold:size=44'
Conky: can't load font 'AvantGarde LT Medium:pixelsize=9'
Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused


```

and it repeats "Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused" forever..

---

### Post by Brandon Williams on 2010-01-31
Is mpd running on your system? If not, remove the the line that contains if_mpd_playing.

There is a line in the config that expects the script /home/david/.scripts/gmail_parser.py to exist, but it doesn't, so you probably want to remove that line, too.

Basically, this particular config requires some other programs to be present, but they aren't. This suggests that maybe this isn't the best .conkyrc for you to use as a template.

---

### Post by Burky on 2010-01-31
Well how do I get this to work?

---

### Post by onyxwolf on 2010-02-02
Ok I'm having some troubles with my conky script too. The weird thing is that mine used to work perfect in Jaunty. Even more weird is the fact that it works half the time on my laptop screen but not on my vga monitor. Any Ideas?


```
background yes
use_xft yes
xftfont CloisterBlack:normal:size=14
xftalpha 0.5
update_interval 3.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 450 5
maximum_width 250
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
border_inner_margin 0
border_width 0
default_color white
color0 Red
color1 Yellow
color7 Blue
color8 White
default_shade_color red
default_outline_color white
alignment top_left
gap_x 0
gap_y 0
text_buffer_size 5120
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale yes
short_units yes

TEXT
#------First tier------------

${image /home/onyxwolf/Conky/Goth_Conky/Images/gargoyle.png -p 0,0 -s 250x170}
${voffset -43}${goto 60}${font CloisterBlack:normal:size=18}Onyxwolf's System
${goto 10}${font CloisterBlack:normal:size=12}${time %a} ${time %b}, ${time %d}${alignr 10}${time %H:%M:%S}
${image /home/onyxwolf/Conky/Goth_Conky/Images/Dragon_Sitting_Final.png  -p 10,50 -s 220x70}

${voffset 5}${goto 10}${font CloisterBlack:normal:size=12}${execi 3600 lsb_release -d | cut -c14-28}${alignr 10}${kernel}

${goto 67}${voffset -5}${font CloisterBlack:normal:size=16}${color}New E-Mail $color${execpi 8 :$((n=`grep -c "X-Mozilla-Status: 0000" "/home/onyxwolf/.thunderbird/rvzsly2g.default/Mail/Local Folders/Inbox"` - 3)); echo $n | xargs /home/onyxwolf/Conky/Goth_Conky/Scripts/colorizeupdates.sh}
#------SYSTEM INFORMATION-----------

${image /home/onyxwolf/Conky/Goth_Conky/Images/nogargoyle.png -p 0,170 -s 250x170}
${voffset -43}${goto 65}${font CloisterBlack:normal:size=18}System Info
${goto 10}${font CloisterBlack:normal:size=12}System Uptime ${alignr 10}${uptime}
${goto 10}${font CloisterBlack:normal:size=12}Core 1 Temp ${alignr 10} ${execpi 8 sensors | grep 'Core\ 0' | cut --characters 15-16 | xargs /home/onyxwolf/Conky/Goth_Conky/Scripts/colorizetemp.sh}°${color}
${goto 10}${font CloisterBlack:normal:size=12}Core 2 Temp ${alignr 10} ${execpi 8 sensors | grep 'Core\ 1' | cut --characters 15-16 | xargs /home/onyxwolf/Conky/Goth_Conky/Scripts/colorizetemp.sh}°${color}
${goto 10}${font CloisterBlack:normal:size=12}Battery State ${alignr 10} ${battery}

${goto 67}${voffset -1}${font CloisterBlack:normal:size=16}${color}New Updates $color${execpi 60 aptitude search "~U" | wc -l | tail | xargs /home/onyxwolf/Conky/Goth_Conky/Scripts/colorizeupdates.sh}
#------FILE SYSTEM-----------

${image /home/onyxwolf/Conky/Goth_Conky/Images/nogargoyle.png -p 0,340 -s 250x170}
${voffset -43}${goto 70}${font CloisterBlack:normal:size=18}File System
${goto 10}${font CloisterBlack:normal:size=12}Hard Disk Temp: ${alignr 10}${execpi 8 /home/onyxwolf/Conky/Goth_Conky/Scripts/hddigitfloat.sh | xargs /home/onyxwolf/Conky/Goth_Conky/Scripts/colorizetemp.sh}°${color}
${goto 10}${font CloisterBlack:normal:size=12}Root: ${goto 85} ${fs_used /} / ${fs_size /}${alignr 10}${fs_free_perc /}%
${goto 10}${font CloisterBlack:normal:size=12}Swap: ${goto 85} ${swap} / ${swapmax}${alignr 10}${swapperc}%
${goto 10}${font CloisterBlack:normal:size=12}Memory: ${goto 85}$mem / $memmax ${alignr 10}${memperc}%${if_mounted /media/disk}
${goto 10}${font CloisterBlack:normal:size=12}${color1}Media: ${alignr 65} ${fs_used /media/disk} / ${fs_size /media/disk}${alignr 10}${fs_free_perc /media/disk}%${image /home/onyxwolf/Conky/Goth_Conky/Images/yellow.png -p 0,340 -s 250x170}${voffset -15}$endif${color}
${goto 67}${voffset 18}${font CloisterBlack:normal:size=16}Disk IO: ${diskio}
#------NETWORK-----------

${image /home/onyxwolf/Conky/Goth_Conky/Images/nogargoyle.png -p 0,510 -s 250x170}${if_existing /proc/net/route ppp0}${voffset -38}${goto 85}${font CloisterBlack:normal:size=18}Tethered
${goto 10}${font CloisterBlack:normal:size=12}IP Address ${alignr 10}${addr ppp0}
${goto 10}${font CloisterBlack:normal:size=12}Up Speed${alignr 10}${upspeed ppp0}
${goto 10}${font CloisterBlack:normal:size=12}Down Speed${alignr 10}${downspeed ppp0}${voffset 30}
${else}${if_existing /proc/net/route eth1}
${voffset -38}${goto 85}${font CloisterBlack:normal:size=18}Wireless
${goto 10}${font CloisterBlack:normal:size=12}WLAN IP ${alignr 10}${addr eth1}
${goto 10}${font CloisterBlack:normal:size=12}External IP ${alignr 10}${execi 3600 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
${goto 10}${font CloisterBlack:normal:size=12}Signal Strength${alignr 10}${execpi 8 nm-tool | grep *^* | grep -n 2 | cut -c 87-90}
${goto 10}${font CloisterBlack:normal:size=12}SSID (AP)${alignr 10}${execpi 8 nm-tool | grep *^* | grep -n 2 | cut -c 8-23 | sed 's/:/\ /g' | sed 's/[ \t]*$//'}${voffset 30}
${else}
${if_existing /proc/net/route eth0}${voffset -38}${goto 85}${font CloisterBlack:normal:size=18}Network
${goto 10}${font CloisterBlack:normal:size=12}LAN IP ${alignr 10}${addr eth0}
${goto 10}${font CloisterBlack:normal:size=12}External IP ${alignr 10}${execi 3600 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
${goto 10}${font CloisterBlack:normal:size=12}Up Speed${alignr 10}${upspeed eth0}
${goto 10}${font CloisterBlack:normal:size=12}Down Speed${alignr 10}${downspeed eth0}${voffset 30}
${else}
${if_existing /proc/net/route ppp0}${voffset 0}${goto 85}${font CloisterBlack:normal:size=18}Tethered
${goto 10}${font CloisterBlack:normal:size=12}IP Address ${alignr 10}${addr ppp0}
${goto 10}${font CloisterBlack:normal:size=12}Up Speed${alignr 10}${upspeed ppp0}
${goto 10}${font CloisterBlack:normal:size=12}Down Speed${alignr 10}${downspeed ppp0}${voffset 0}${else}${voffset -65}${goto 65}${font CloisterBlack:normal:size=18}No Network

${goto 10}${font CloisterBlack:normal:size=14}Connection cannot be determined
${voffset 29}
${endif}${endif}${endif}${endif}${if_existing /proc/net/route tunsnx}${image /home/onyxwolf/Conky/Goth_Conky/Images/yellow.png -p 0,510 -s 250x170}
${goto 40}${voffset -33}${font CloisterBlack:normal:size=15}${color1}VPN ${addr tunsnx}${voffset -25}
${endif /proc/net/route tunsnx}${color}
#------PROCCESS-----------

${image /home/onyxwolf/Conky/Goth_Conky/Images/bottomgargoyle.png -p 0,680 -s 250x170}
${voffset -40}${goto 53}${font CloisterBlack:normal:size=20}Top Processes
${goto 10}${font CloisterBlack:normal:size=12}${color}${top name 1}${alignr 10}${top pid 1}${top cpu 1}${top mem 1}
${goto 10}${font CloisterBlack:normal:size=12}${color}${top name 2}${alignr 10}${top pid 2}${top cpu 2}${top mem 2}
${goto 10}${font CloisterBlack:normal:size=12}${top name 3}${alignr 10}${top pid 3}${top cpu 3}${top mem 3}
${goto 10}${font CloisterBlack:normal:size=12}${top name 4}${alignr 10}${top pid 4}${top cpu 4}${top mem 4}
${goto 70}${voffset 16}${font CloisterBlack:normal:size=16}Conky ${conky_version}
```

---

### Post by onyxwolf on 2010-02-02
Ok to clear things up, my script is a heavily modified version of dmillerct Goth_Conky script. So just wanted to through my props his/her way since I'm posting it.

---

### Post by onyxwolf on 2010-02-02
I figured mine out. I first backed up my conky.conf then deleted it and it ran fine. Ugly but fine. so I made a conky2 script in my home folder and deleted all but one section for each section. It worked for all but my networking one. I tried to see which command was causing the problem. Turned out to be:
${execpi 8 nm-tool | grep *^* | grep -n 2 | cut -c 87-90}
${execpi 8 nm-tool | grep *^* | grep -n 2 | cut -c 8-23 | sed 's/:/\ /g' | sed 's/[ \t]*$//'}

so I ran the command in terminal and it was giving me a process warning
** (process:5616): WARNING **: "Tried to set deprecated property gsm/band"
????
After googling it, I remembered I had been missing around with nm (network manager)'s broadband connections and still had it there. Deleted the connection and boom works like a charm. WEIRD!!!

---

