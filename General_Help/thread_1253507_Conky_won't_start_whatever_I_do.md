---
title: "Conky won't start whatever I do"
date: 2009-08-30
forum: General Help
---

### Post by tezer on 2009-08-30
Hi
strange, strange, strange conky...
It does not start at start up of my computer. I start it in a "proper" way:
I call a script at start up:
```
#!/bin/bash
/bin/sleep 20
/usr/bin/conky -d -c ~/.conkyrc > /dev/null 2>&1
```

I tried *sleep 10* up to *sleep 120*
I also tried all other versions of the script and nothing helps...

But it is not the whole story.
I wrote a small script to (re-)load conky manually:
```
#!/bin/bash
pkill conky && conky &
```
And it does not work after my computer's start up!

The only way to start conky is to open terminal and type in "conky". It is also possible to start from Alt+2. After it the reload script starts working.

Here is my .conkyrc:
```
background yes
#font 7x13

#on_bottom yes

#mpd_host 192.168.150.2
#mpd_port 6600

update_interval 1.0

total_run_times 0

own_window yes
own_window_type desktop # Try also 'normal' or 'override'  desktop

own_window_transparent yes

double_buffer yes

minimum_size 280 5

draw_shades no
draw_outline no
draw_borders no
stippled_borders 8
#border_margin 4
border_width 1

default_color white
default_shade_color black
default_outline_color black

alignment top_right

maximum_width 245

gap_x 12
gap_y 110

no_buffers yes

uppercase none

cpu_avg_samples 2
net_avg_samples 2

use_xft yes
override_utf8_locale yes
use_spacer none
xftalpha 0.9
xftfont Candera:size=8

format_human_readable yes


# stuff after 'TEXT' will be formatted on screen

TEXT
$nodename${alignr}linux-$kernel
${time %D}${alignr}${time %T}

System ${hr}
Uptime:$uptime - Load: $loadavg
 CPU Frequency: $freq_g
 CPU Usage: $cpu% ${cpubar}
${cpugraph cpu0 16,244 000000 000000}
 RAM Usage: $mem/$memmax - $memperc% ${membar}
 Swap Usage: $swap/$swapmax - $swapperc% ${swapbar}
 Processes: $processes  Running: $running_processes

Networking ${hr}
 Down: ${downspeed eth0} k/s${offset 80}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 16,120 000000 000000} ${upspeedgraph eth0 16,120 000000 000000}
 Address: ${addr eth0}${alignr}TCP Connections: ${tcp_portmon 1 65535 count}

File Systems ${hr}
 / ${fs_used /}/${fs_size /} ${fs_bar /}
 ~ ${fs_used /home}/${fs_size /home} ${fs_bar /home}

Name${alignr}PID   CPU%  MEM%
 ${top name 1}${alignr}${top pid 1}  ${top cpu 1}    ${top mem 1}
 ${top name 2}${alignr}${top pid 2}  ${top cpu 2}    ${top mem 2}
 ${top name 3}${alignr}${top pid 3}  ${top cpu 3}    ${top mem 3}
Mem usage
 ${top_mem name 1} ${alignr}${top_mem pid 1}  ${top_mem cpu 1}   ${top_mem mem 1}
 ${top_mem name 2} ${alignr}${top_mem pid 2}  ${top_mem cpu 2}   ${top_mem mem 2}
 ${top_mem name 3} ${alignr}${top_mem pid 3}  ${top_mem cpu 3}   ${top_mem mem 3}

Local Weather ${hr}
${alignc 20}${execi 3600 conkyForecast --datatype=CC}${alignr}${color1}&#1057;&#1077;&#1081;&#1095;&#1072;&#1089;: ${color}${execi 3600 conkyForecast --datatype=LT}
${font ConkyWeather:size=45}${execi 3600 conkyForecast --datatype=WF}$font
${alignc 0}${voffset -45}${font size=15}${execi 3600 conkyForecast --datatype=HT}$font                           
${alignr}${voffset -35}${color1}&#1042;&#1077;&#1090;&#1077;&#1088;: $color${execi 3600 conkyForecast --datatype=WS}$font
${alignc}                                                                    $font${font arrows:size=15}${execi 3600 conkyForecast --datatype=BF}$font
${alignr}${color1}&#1042;&#1083;&#1072;&#1078;&#1085;&#1086;&#1089;&#1090;&#1100;: $color${execi 3600 conkyForecast --datatype=HM}$font
${alignr}${execi 3600 conkyForecast --datatype=BR} - ${execi 3600 conkyForecast --datatype=BD}$color$font

${stippled_hr}
${font ConkyWeather:size=30}${execi 3600 conkyForecast --location=UKXX0215 --startday=1 --endday=4 --datatype=WF --spaces=2}$font
${execi 3600 conkyForecast --location=UKXX0215 --template=/home/taras/Programs/conkyScripts/conkyforecast/templates/t1}
Calendar ${hr}
${execi 1800 conkyGoogleCalendar -u username -p password -r "some calendar" -n}
```

I tried a shortened version of it deleting everything before TEXT as well as the weather and google calendar sections. No change in behaviour...

---

### Post by ecmatter on 2009-08-30
Maybe try a simpler script?  This one works for me:

```

#!/bin/bash

sleep 20
conky

```

Make sure that your script is located in a directory in your PATH.

---

### Post by tezer on 2009-08-30
> **ecmatter said:**
> Maybe try a simpler script?  This one works for me:

```

#!/bin/bash

sleep 20
conky

```

Make sure that your script is located in a directory in your PATH.

I tried all different variants of the script... As for the script it is called from the start up using its path: ~/scripts/conky.sh
When I start it manually it works fine. But not at the start up...

---

### Post by SuaSwe on 2009-08-30
Is your script in a hidden file? Most tutorials that I've come across suggest something like ~/scripts/.conky.sh (e.g. hidden), in which case the path also needs to refer to a hidden file. 

What exactly do you have for your Conky entry in System -> Preferences -> Startup Applications?

I have:

> 
Name: Conky
Command: /home/suave/.scripts/.conky_start.sh
Comment: Conky Startup Config


and my .conky_start.sh file looks like

```

#!/bin/bash
sleep 10 &&
conky &
exit

```

---

### Post by SuaSwe on 2009-08-30
I also seem to recall that the path needs to be e.g.

**/home/**suave/.scripts etc

and not

~/suave/.scripts etc

---

### Post by tezer on 2009-08-31
The script and the path are ok.
Any more ideas?

---

### Post by rdionicio on 2009-08-31
> **tezer said:**
> The script and the path are ok.
Any more ideas?

Have you tried changing .scripts to just scripts as unhidden? Does conky look for .scripts?

---

### Post by tezer on 2009-08-31
> **rdionicio said:**
> Have you tried changing .scripts to just scripts as unhidden? Does conky look for .scripts?
Yes. And it finds it if I type "conky" in terminal... I do not understand why it does not do it on start up and when I run the restart script. Once I start it from terminal (or Alt+F2, or Alt+F3). The restart script works just fine..

---

### Post by rdionicio on 2009-08-31
Try moving your startup script to your home folder.. out of the scripts folder. Then reflect those changes in the Startup Applications.

---

### Post by tezer on 2009-09-01
> **rdionicio said:**
> Try moving your startup script to your home folder.. out of the scripts folder. Then reflect those changes in the Startup Applications.

Nothing helps. The only difference: I was able to use the restart script without manual start of conky.

---

### Post by tezer on 2009-09-03
Anyone? ANY ideas about what's wrong?

---

