---
title: "Conky Delay"
date: 2009-08-25
forum: General Help
---

### Post by rdionicio on 2009-08-25
On my conky script it shows the CPU and RAM utilization as well as time. I thought it was supposed to update in real time but it only updates every 5 minutes. Here is my conky script that I copied from elsewhere.

```
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
color1 F8DF58



TEXT
 ${color 6694B2}${font OpenLogos:size=45} u t
${color BADCDD}${font weather:size=82}${execi 600 ~/scripts/conditions.sh}${color}${font}${voffset -25}  ${execi 1200 ~/scripts/pogodynka.sh}

   ${font weather:size=28}x ${font}HDD ${execi 1 ~/scripts/hddmonit.sh}°C 
    
   ${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth1} Kb/s 
   ${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth1} Kb/s 

   ${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth1}
   ${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth1}

   ${color ffffff}${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
   ${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}

   ${color F8DF58}${font StyleBats:size=16}8${font}  Battery: ${battery_percent}% ${battery_bar}

   ${color F8DF58}${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py "username" "password" 3}

   ${color C2E078}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

   ${font StyleBats:size=18}P${font}  Work:  ${uptime_short}


 ${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %H:%M}
```

---

### Post by stinkeye on 2009-08-25
Add this to your conky above text.```
background yes
update_interval 1.0
total_run_times 0
```
This is a better forum for conky help.
[[COLOR="DarkRed"]_Post your .conkyrc files w/ screenshots_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=281865")
Tons of friendly advice and ideas on your path to conky addiction.

---

### Post by rdionicio on 2009-08-25
> **stinkeye said:**
> Add this to your conky above text.```
background yes
update_interval 1.0
total_run_times 0
```
This is a better forum for conky help.
[[COLOR="DarkRed"]_Post your .conkyrc files w/ screenshots_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=281865")
Tons of friendly advice and ideas on your path to conky addiction.

Thanks I'll try that out and thanks for directing me to that page.

---

### Post by rdionicio on 2009-08-25
After adding those commands it still wasnt updating but I figured out what was happening. The gmail script that's part of the conky configuration was spitting out errors so when I removed it the refreshing was back to normal. I checked the gmail python script again and I had a typo with my username and password. That's what I think was hanging it up.

---

### Post by tgeer43 on 2009-08-25
Also check your 'execi' and 'execpi' commands. The number immediately following the command (eg. execi 600) is the number of seconds between each execi or execpi call. For instance, your weather conditions script is set to update every 5 minutes. Of course you wouldn't want that one updating every second but you get the picture.

tgeer

---

### Post by rdionicio on 2009-08-25
> **tgeer43 said:**
> Also check your 'execi' and 'execpi' commands. The number immediately following the command (eg. execi 600) is the number of seconds between each execi or execpi call. For instance, your weather conditions script is set to update every 5 minutes. Of course you wouldn't want that one updating every second but you get the picture.

tgeer

Thanks for explaining this to me. It helped me understand the syntax which will be helpful for me in the future if I may want to add something. Everything is working just fine now :popcorn:

---

