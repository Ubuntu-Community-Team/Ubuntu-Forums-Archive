---
title: "multiple conky clocks and time zones"
date: 2010-11-02
forum: General Help
---

### Post by GrouchyGaijin on 2010-11-02
Hi All,

I've been playing around with conky for a week or so and am having a lot of fun.  I'm not sure how to do this though and need some pointers.

I have a conky clock script that works and I have the first clock on the screen where I want it.

I'd like to change the timezone of that clock to Japan.  I'm going to add two more clocks with different time zones. (All three zones are different from my timezone.)

Questions:

Using the conkyrc below how can I change the timezone to Japan?
I'd like the time to be in 24 hour format and if the date would also match the time that would be great.

```
## Conky Clock Widget          ##
## by jpope                    ##
## version 1.1.2010.10.24      ##
##       - 1.0.2010.10.19      ##
##                             ##
#################################
# &#8212; Conky settings &#8212; #
background no
update_interval 1
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale yes
double_buffer yes
no_buffers yes
text_buffer_size 1024
imlib_cache_size 0

# &#8212; Window specifications &#8212; #
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,sticky,skip_taskbar,skip_pager,below
border_inner_margin 0
border_outer_margin 0
minimum_size 175 175
maximum_width 175
alignment middle_left
gap_x 16
gap_y 16

# &#8212; Graphics settings &#8212; #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# &#8212; Text settings &#8212; #
use_xft yes
xftfont Oloron\ Tryout:size=8
# Font available from http://www.dafont.com/oloron.font
xftalpha 0
use_spacer left
uppercase no

# &#8212; Color settings &#8212; #
default_color ffffff
color1 bbbbbb
color2 999999
color3 eeeeee

# &#8212; Lua Load &#8212; #
lua_load ~/.config/conky/clockwidget/conkyclock.lua
lua_draw_hook_pre widgets

TEXT
${if_match ${execpi 1 cat ~/.config/conky/clockwidget/clockswitch} == 0}${image ~/.config/conky/clockwidget/images/bckgnd.png p 0x0}
${voffset 52}${font Oloron\ Tryout:size=8}${color1}${alignc}${time %b}${font}
${voffset 0}${font Oloron\ Tryout:size=16}${color2}${goto 62}${time %I}${color}${alignr 63}${time %M}${font}
${font Oloron\ Tryout:size=8}${voffset 0}${color1}${alignc}${time %d}${font}${else}
${image ~/.config/conky/clockwidget/images/bckgnd_plain.png p 0x0}${font Oloron\ Tryout:size=18}${color1}${alignc}${time %B}${font}${endif}
```

---

