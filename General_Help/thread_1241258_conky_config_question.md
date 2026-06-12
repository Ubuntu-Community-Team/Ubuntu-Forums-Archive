---
title: "conky config question"
date: 2009-08-15
forum: General Help
---

### Post by rifak on 2009-08-15
hey everyone,
i am trying to set up a calendar scheme in conky and it doesn't want to overlap. im trying to get the next two months to show in one line, next to each other, but when i use the voffset and goto commands, it only moves the name of the month. heres .conkyrc

font Snap.se:size=8
xftfont Snap.se:size=8
use_xft yes
xftalpha 0.1
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 210 5
maximum_width 280
default_color white
default_shade_color 000000
default_outline_color 000000
alignment top_right
text_buffer_size 1024
gap_x 6
gap_y 22
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer none

TEXT
${font LCDDisplayCapsSSi:style=Bold:pixelsize=40}${time %l:%M %p}${font Snap.se:size=10}
${alignr}${time %A, %B %e %G}

${font Aerial:style=Bold:pixelsize=12}CALENDAR${font Snap.se:size=8}${hr 1}

${font DejaVu Sans Mono :size=12}${exec cal}
${font DejaVu Sans Mono :size=6}${exec cal sept 2009}
${voffset -75}${goto 100}${font DejaVu Sans Mono :size=6}${exec cal oct 2009}
${voffset 15}${font Aerial:style=Bold:pixelsize=12}WEATHER${font Snap.se:size=8}${hr 1}
${font Aerial:pixelsize=10}${execi 600 weather home}

${font Aerial:style=Bold:pixelsize=12}EMAIL${font Snap.se:size=8} ${hr 1 }
You have ${color #EAF81F}${texeci 30 perl ~/Customization/conky/scripts/gmail.pl n} ${color}new email(s).

${color #EAF81F}${execi 30 perl ~/Customization/conky/scripts/gmail.pl s}${color}

and i posted a screenshot of the conky also. even if i could get a single command to make this happen. something like "cal -3" but just show the next two months, rather than last, this, next month.

---

