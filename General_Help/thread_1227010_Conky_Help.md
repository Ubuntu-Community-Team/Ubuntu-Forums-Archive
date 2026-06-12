---
title: "Conky Help"
date: 2009-07-30
forum: General Help
---

### Post by Holmes89 on 2009-07-30
Whenever I start conky instead of it integrating with my background it pops up in a little side window, how do I fix this?

---

### Post by wojox on 2009-07-30
Post .conkyrc up here and lets take a look.

---

### Post by Holmes89 on 2009-07-30
Well I borrowed this [one]("http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/") just so I could get started and was going to tweak it from there.

---

### Post by Holmes89 on 2009-07-30
> **wojox said:**
> Post .conkyrc up here and lets take a look.

Okay this is what I have:

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

   ${color F8DF58}${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py ************ ********** 3}

   ${color C2E078}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

   ${font StyleBats:size=18}P${font}  Work:  ${uptime_short}


 ${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %H:%M}

```

This is what I get in the terminal when I run Conky

```
Conky: use_spacer should have an argument of left, right, or none.  'no' seems to be some form of 'false', so defaulting to none.
Conky: desktop window (14000a7) is subwindow of root window (7f)
Conky: window type - normal
Conky: drawing to created window (0x4600002)
Conky: drawing to single buffer

```

Now I have my Conkyrc file in my home directory... is this right?

---

### Post by wojox on 2009-07-30
Change to:

use_spacer yes

and it should be in your home folder yes.
.conkyrc

---

