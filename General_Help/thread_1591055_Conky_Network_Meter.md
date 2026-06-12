---
title: "Conky Network Meter"
date: 2010-10-08
forum: General Help
---

### Post by Jonny87 on 2010-10-08
I'm trying to get a network meter working on conky that shows total weekly and monthly Upload and Download. For some reason they don't show any stats, just the headings.
Heres what I have so far;
```
Weekly Down: ${execi 300 vnstat -w | grep "`date +"%b '%y"`" | awk '{print $3 $4}'} ${alignr}WeeklyUp: ${execi 300 vnstat -w | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}
Monthly Down: ${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'} ${alignr}Monthly Up: ${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}
```

Also if possible I'd like one that shows an indefinite amount that never resets unless I some how reset it.
Can any one help with these two things?

---

### Post by Jonny87 on 2010-10-08
Ok I've got a bit closer with the network meter but its still not quite right.
Heres the code;
```
${font DejaVu Sans Mono:bold:size=9}${color5}Yesterday:${color3} ${execi 300 vnstat | grep "yesterday" | awk '{print $2 $3}'}${goto 140}${color9}${execi 300 vnstat | grep "yesterday" | awk '{print $5 $6}'}${goto 205}${color5}${execi 300 vnstat | grep "yesterday" | awk '{print $8 $9}'}
    ${color5}Today:${color3} ${execi 300 vnstat | grep "today" | awk '{print $2 $3}'}${goto 140}${color9}${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}${goto 205}${color5}${execi 300 vnstat | grep "today" | awk '{print $8 $9}'}
     ${color5}Week: ${color3}${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'}${goto 140}${color9}${execi 300 vnstat -w | grep "current week" | awk '{print $6 $7}'}${goto 205}${color5}${execi 300 vnstat -w | grep "current week" | awk '{print $9 $10}'}
    ${color5}Month: ${color3}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${goto 140}${color9}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}${goto 205}${color5}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $9 $10}'}${font}
```

And attached is what it shows.

It doesn't quite look like what I'm after, any ideas?

---

### Post by dmillerct on 2010-10-08
> **Jonny87 said:**
> Ok I've got a bit closer with the network meter but its still not quite right.
Heres the code;
```
${font DejaVu Sans Mono:bold:size=9}${color5}Yesterday:${color3} ${execi 300 vnstat | grep "yesterday" | awk '{print $2 $3}'}${goto 140}${color9}${execi 300 vnstat | grep "yesterday" | awk '{print $5 $6}'}${goto 205}${color5}${execi 300 vnstat | grep "yesterday" | awk '{print $8 $9}'}
    ${color5}Today:${color3} ${execi 300 vnstat | grep "today" | awk '{print $2 $3}'}${goto 140}${color9}${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}${goto 205}${color5}${execi 300 vnstat | grep "today" | awk '{print $8 $9}'}
     ${color5}Week: ${color3}${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'}${goto 140}${color9}${execi 300 vnstat -w | grep "current week" | awk '{print $6 $7}'}${goto 205}${color5}${execi 300 vnstat -w | grep "current week" | awk '{print $9 $10}'}
    ${color5}Month: ${color3}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${goto 140}${color9}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}${goto 205}${color5}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $9 $10}'}${font}
```

And attached is what it shows.

It doesn't quite look like what I'm after, any ideas?

What don't you like about it? As an avid conky-er I highly recommend that you visit the following thread:
[http://ubuntuforums.org/showthread.php?t=281865&goto=newpost]("http://ubuntuforums.org/showthread.php?t=281865&goto=newpost") and post your query there. There are lots of us that just love to help out with conky configurations.

You also might want to check out Conky-Hardcore a great online resource for tips and tricks with your conky config:

[http://conkyhardcore.com/]("http://conkyhardcore.com/")

---

### Post by Jonny87 on 2010-10-08
> **dmillerct said:**
> What don't you like about it? As an avid conky-er I highly recommend that you visit the following thread:
[http://ubuntuforums.org/showthread.php?t=281865&goto=newpost](http://ubuntuforums.org/showthread.php?t=281865&goto=newpost) and post your query there. There are lots of us that just love to help out with conky configurations.

You also might want to check out Conky-Hardcore a great online resource for tips and tricks with your conky config:

[http://conkyhardcore.com/](http://conkyhardcore.com/)

Thanks for the link,

Well I was kinda hoping that it would update like the following;
```
Session Total Down: ${color #FD7171}${totaldown eth0}${color} ${alignr}Total Up: ${color #11AD11}${totalup eth0}${color}
```

That one keeps updating as the rest of conky updates.

---

### Post by stinkeye on 2010-10-08
Here's one I use.
```
background yes
font Sans Seriff:size=9
xftfont DejaVu Sans Mono:bold:size=10
use_xft yes
xftalpha 0.8
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 300
maximum_width 300
default_color 919FAA
default_shade_color 333333
default_outline_color 00ff00
alignment br
gap_x 10
gap_y 10
no_buffers yes
cpu_avg_samples 2
override_utf8_locale yes
uppercase no # set to yes if you want all text to be in uppercase
use_spacer right

# colours
#off white
color1 BDAC88

# cream
color2 D2B16A

# cyan
#color3 08A1A1

# bluemoon
color3 919FAA

# yellow
color4 F1BC49

# Green
color5 00940F

#dark cyan
color6 074C4C


#grey
color7 6b6b6b

#orange
color8 AF560D

#yellow
color9 F1BC49

#lua_load /home/glen/conky/draw_bg.lua
#lua_draw_hook_pre draw_bg

TEXT
${goto 90}${color1}${font DejaVu Sans Mono:bold:size=12}INTERNET USAGE
${goto 90}${voffset -15}______________
${goto 90}${font DejaVu Sans Mono:bold:size=10}${color3}Down${goto 170}${color9}Up${goto 235}${color5}Total
${goto 10}${font DejaVu Sans Mono:bold:size=9}${color1}Yesterday: ${color3}${execi 300 vnstat | grep "yesterday" | awk '{print $2 $3}'}${goto 170}${color9}${execi 300 vnstat | grep "yesterday" | awk '{print $5 $6}'}${goto 235}${color5}${execi 300 vnstat | grep "yesterday" | awk '{print $8 $9}'}
${goto 10}    ${color1}Today: ${color3}${execi 300 vnstat | grep "today" | awk '{print $2 $3}'}${goto 170}${color9}${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}${goto 235}${color5}${execi 300 vnstat | grep "today" | awk '{print $8 $9}'}
${goto 10}     ${color1}Week: ${color3}${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'}${goto 170}${color9}${execi 300 vnstat -w | grep "current week" | awk '{print $6 $7}'}${goto 235}${color5}${execi 300 vnstat -w | grep "current week" | awk '{print $9 $10}'}
${goto 10}    ${color1}Month: ${color3}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${goto 170}${color9}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}${goto 235}${color5}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $9 $10}'}${font}
```

---

### Post by Jonny87 on 2010-10-08
> **stinkeye said:**
> Here's one I use.
```
background yes
font Sans Seriff:size=9
xftfont DejaVu Sans Mono:bold:size=10
use_xft yes
xftalpha 0.8
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 300
maximum_width 300
default_color 919FAA
default_shade_color 333333
default_outline_color 00ff00
alignment br
gap_x 10
gap_y 10
no_buffers yes
cpu_avg_samples 2
override_utf8_locale yes
uppercase no # set to yes if you want all text to be in uppercase
use_spacer right

# colours
#off white
color1 BDAC88

# cream
color2 D2B16A

# cyan
#color3 08A1A1

# bluemoon
color3 919FAA

# yellow
color4 F1BC49

# Green
color5 00940F

#dark cyan
color6 074C4C


#grey
color7 6b6b6b

#orange
color8 AF560D

#yellow
color9 F1BC49

#lua_load /home/glen/conky/draw_bg.lua
#lua_draw_hook_pre draw_bg

TEXT
${goto 90}${color1}${font DejaVu Sans Mono:bold:size=12}INTERNET USAGE
${goto 90}${voffset -15}______________
${goto 90}${font DejaVu Sans Mono:bold:size=10}${color3}Down${goto 170}${color9}Up${goto 235}${color5}Total
${goto 10}${font DejaVu Sans Mono:bold:size=9}${color1}Yesterday: ${color3}${execi 300 vnstat | grep "yesterday" | awk '{print $2 $3}'}${goto 170}${color9}${execi 300 vnstat | grep "yesterday" | awk '{print $5 $6}'}${goto 235}${color5}${execi 300 vnstat | grep "yesterday" | awk '{print $8 $9}'}
${goto 10}    ${color1}Today: ${color3}${execi 300 vnstat | grep "today" | awk '{print $2 $3}'}${goto 170}${color9}${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}${goto 235}${color5}${execi 300 vnstat | grep "today" | awk '{print $8 $9}'}
${goto 10}     ${color1}Week: ${color3}${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'}${goto 170}${color9}${execi 300 vnstat -w | grep "current week" | awk '{print $6 $7}'}${goto 235}${color5}${execi 300 vnstat -w | grep "current week" | awk '{print $9 $10}'}
${goto 10}    ${color1}Month: ${color3}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${goto 170}${color9}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}${goto 235}${color5}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $9 $10}'}${font}
```

Thanks, It looks much the same.
Does yours keep updating? Or is that not possible or do I need to configure some thing else?

---

### Post by dmillerct on 2010-10-08
When you use ${execi 300 xxx} The 300 represents the number of seconds used to execute the command. See conky variables here:
[http://conky.sourceforge.net/variables.html]("http://conky.sourceforge.net/variables.html")

This of course wont be faster than update_interval located above TEXT in the conky configuration file. For example if execi is executing ever 5 seconds but update_interval is set to 10 seconds you will only see the data every 10 seconds.

---

### Post by Jonny87 on 2010-10-08
> **dmillerct said:**
> When you use ${execi 300 xxx} The 300 represents the number of seconds used to execute the command. See conky variables here:
[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

This of course wont be faster than update_interval located above TEXT in the conky configuration file. For example if execi is executing ever 5 seconds but update_interval is set to 10 seconds you will only see the data every 10 seconds.

Thanks again for the link.
I've reset the seconds but still no changes. Is there some thing else with "vnstat" that I have to configure?

---

### Post by dmillerct on 2010-10-08
> **Jonny87 said:**
> Thanks again for the link.
I've reset the seconds but still no changes. Is there some thing else with "vnstat" that I have to configure?

No should't be. Are you sure you are using the internet enough in between? :)

---

### Post by Jonny87 on 2010-10-08
It only seems to chage if I run;
```
sudo vnstat -u -i eth0
```
from the terminal.

---

### Post by Jonny87 on 2010-10-09
I got it updating.
I added the following line to the start of it.
```
${execi 10 vnstat -u -i eth0}
```

I'd still like to know how to do one that would show the full total regardless of months or weeks.
Wondering if the following would work;
```
Total: ${execi 10 vnstat | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${goto 170}${execi 10 vnstat | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}${goto 235}${execi 10 vnstat | grep "`date +"%b '%y"`" | awk '{print $9 $10}'}
```

My vnstat data base was only started to day so can't tell, it just shows the same as the other sections. Can some one try it on their system and let me know or just confirm if you happen to know?

---

### Post by layr on 2011-06-05
This script doesn't output any data :/

Might the fact i'm using 3G internet have anything to do with this?
(i'm after for monthly DL/UL output)

---

