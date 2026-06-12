---
title: "problem with conky"
date: 2010-03-25
forum: General Help
---

### Post by dluzius on 2010-03-25
[B][SIZE="4"][SIZE="6"][COLOR="#000000"]I've messed around adding things to my conky file, and now when displayed it is beautiful, except there are duplicate lines of text in black, almost in the background. How do I get rid of them.
    Dave[/COLOR][/SIZE][/SIZE][/B]

---

### Post by stinkeye on 2010-03-25
Can't help unless you post your conky config.

---

### Post by dluzius on 2010-03-25
[B]here's the source file for my conky:

background		no
use_xft			yes
xftfont			Courier:size=16
double_buffer		yes
update_interval		2
alignment		tm
gap_x			10
gap_y			10
no_buffers		yes
minimum_size 		365x500
pad_percents		3
[/B][/COLOR][/COLOR]
TEXT


${font :size=16}
${color green}$nodename - $sysname $kernel
${color yellow}Uptime: $uptime

${color red}RAM: $memperc% ${membar 8}
Swap:$swapperc% ${swapbar 8}
CPU: $cpu% ${cpubar 8}
${color #FFFF00}
HDD USAGE ${hr 1}
       ${fs_used /}/${fs_size /}${alignr}${fs_used_perc /}%
${fs_bar 8 /}
${color #00FF00}Down: ${downspeedf eth0}k/s ${alignr}${totaldown eth0} total
${downspeedgraph eth0}
${color #00FF00}Up: ${upspeedf eth0}k/s ${alignr}${totalup eth0} total
${upspeedgraph eth0}

${color orange} ${font :size=30}$alignc${time %H:%Mh}
TIA

---

### Post by stinkeye on 2010-03-25
At the moment it's not drawing your text shading correctly.
I haven't figured out why yet.

If you add
```
draw_shades no
```
to your conky config above "TEXT" it will fix for now.

PS. To add copied text and stuff its better to click on the # icon
and then paste between the code blocks.

---

### Post by dluzius on 2010-03-25
[B]thanks, stinkeye, that solved the problem. 
But why does my conky display disappear when I close Terminal.
I am calling it up by using the command conky &, but that only helps sometimes.
  Tia, DAve[/B]

---

### Post by Amof on 2010-03-25
> **dluzius said:**
> [B]thanks, stinkeye, that solved the problem. 
But why does my conky display disappear when I close Terminal.
I am calling it up by using the command conky &, but that only helps sometimes.
  Tia, DAve[/B]


When you close the terminal you kill all the programs that were started from that terminal (with exceptions).

Easiest way to start conky on the fly is press ALT - F2 and type "conky".

---

### Post by stinkeye on 2010-03-25
Heres a script to toggle your conky on/off.
Save as toggleconky

Make executable by right clicking
properties > permissions and tick execute.
Create a launcher in the panel or on the desktop linked to where you saved the script.
```
#!/bin/sh

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
 exec conky -c [COLOR="Red"]~/path/to/your/conky[/COLOR] &
fi
```
[COLOR="#ff0000"]change to path to your conky[/COLOR]


Have a look at this post.
Should answer most of your conky questions.
[**_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

---

