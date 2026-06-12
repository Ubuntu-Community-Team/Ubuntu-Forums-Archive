---
title: "Any application to check daily internet usage ?"
date: 2012-04-25
forum: General Help
---

### Post by sandip250382 on 2012-04-25
Pals, I need to monitor my daily Internet usage as well as monthly figure. I have Ubuntu 11.10 installed in my laptop. So anyone have any idea about any such tool/application which can give my daily Internet usage statistics as well as monthly one.

Any inputs will be great for me.

---

### Post by stinkeye on 2012-04-25
Can use vnstat.
```
sudo apt-get install vnstat
```

Create a database...
```
sudo vnstat -u -i [COLOR="Magenta"]eth0[/COLOR]
```
[COLOR="magenta"]Your network interface.[/COLOR]

Then to view (see **man vnstat**)
```
vnstat
```


You can also use conky to display vnstat data on the desktop.
Save this as **.conkyrc** in your home folder.
```
background yes
font Sans Seriff:size=9
xftfont DejaVu Sans Mono:bold:size=10
use_xft yes
xftalpha 0.8
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent no
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

Install conky...
```
sudo apt-get install conky-all
```

To run... 
```
conky
```

and you should see similar to pic in the bottom right corner.

---

### Post by sandip250382 on 2012-04-25
> **stinkeye said:**
> Can use vnstat.
```
sudo apt-get install vnstat
```Create a database...
```
sudo vnstat -u -i [COLOR=Magenta]eth0[/COLOR]
```[COLOR=magenta]Your network interface.[/COLOR]

Then to view (see **man vnstat**)
```
vnstat
```
You can also use conky to display vnstat data on the desktop.
Save this as **.conkyrc** in your home folder.
```
background yes
font Sans Seriff:size=9
xftfont DejaVu Sans Mono:bold:size=10
use_xft yes
xftalpha 0.8
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent no
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
```Install conky...
```
sudo apt-get install conky-all
```To run... 
```
conky
```and you should see similar to pic in the bottom right corner.


WOW! Conky is great. Thanks a lot mate.

---

### Post by stinkeye on 2012-04-25
> **sandip250382 said:**
> WOW! Conky is great. Thanks a lot mate.

No problem.
Conky is one of my favourites.
Run 6 configs on the desktop.

---

### Post by codemaniac on 2012-04-25
Here is my conky that captures my wireless interface's upload/download usages .

---

