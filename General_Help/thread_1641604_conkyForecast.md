---
title: "conkyForecast"
date: 2010-12-09
forum: General Help
---

### Post by Forged on 2010-12-09
conkyForecast is giving me the way wrong temperature (conky says it is 129 but weather.com says it is 54) it also added an A symbol before the degree symbol. 

[[img]http://imgur.com/yVYqW.jpg[/img]](http://imgur.com/yVYqW.jpg)

conkyForecast.template
```

${image [--datatype=WI --CC] -p 0,0 -s 64x64}
${image [--datatype=WI --startday=1] -p 120,0 -s 64x64}
${image [--datatype=WI --startday=2] -p 240,0 -s 64x64}
${voffset 15}
Now: [--datatype=LT]${goto 135}[--datatype=DW --startday=1]: [--datatype=LT --startday=1]${goto 255}[--datatype=DW --startday=2]: [--datatype=LT --startday=2]

```

conkyrc
```

# conky configuration
# edited by Mark Buck (Kaivalagi) <m_buck@hotmail.com>

# set to yes if you want Conky to be forked in the background
background no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

# Text alpha when using Xft
xftalpha 0.8

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

background yes
own_window yes
own_window_transparent yes

own_window_type desktop
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

draw_borders no
draw_shades no

gap_x 30
gap_y 30
alignment top_right

update_interval 1
default_color white

use_xft yes
xftfont Sans:bold:size=7

use_spacer none

cpu_avg_samples 2
net_avg_samples 2
no_buffers yes
text_buffer_size 2048

minimum_size 310 0
maximum_width 0

override_utf8_locale ye

TEXT
${execpi 1800 conkyForecast --location=78015 --template=~/conkyForecast.template -i -w}

```

---

### Post by fenario on 2010-12-29
Hello Friend

I can already see a solution for you.
In your conkyrc you forgot the "s" in yes for "override_utf8_locale yes"
just before TEXT at the bottom
this will make the A next to temp go away (I hope)
and for location you use what seems to be a postcode.
It needs to be USTX0058 which means USA Texas Nr 58
which is Austin
you can find the code by doing:
[http://xoap.weather.com/search/search?where=Austin,Texas](http://xoap.weather.com/search/search?where=Austin,Texas)
or wherever you live

I'm surprised that you had no answers in 2 weeks.
Hope this will help you and you have enough time;
as once you start tweaking you get the conky fever
and there is no stopping.

Ciao Fenario

---

