---
title: "Conky help needed."
date: 2011-01-13
forum: General Help
---

### Post by bigswagg on 2011-01-13
when i add this i get the "Too many special things for text" error on Conky.... any idea?

```

##############################################
#  Settings
##############################################
background no
use_xft yes
xftfont Sans-Serif:size=8
xftalpha 1
update_interval 1.0
total_run_times 0
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 200
maximum_width 200
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color green
default_shade_color black
default_outline_color white
alignment top_right
gap_x 20
gap_y 20
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale yes
color1 222222

TEXT
${font Sans-Serif:bold:size=12}
${color}I T ${color1}L ${color}I S ${color1}A S T I M E
${if_match  ${exec date +"%M"} < 35}${if_match ${exec date +"%M"} >=  15}${if_match ${exec date +"%M"} < 20}${color}${endif}${endif}A  ${color1}C ${if_match ${exec date +"%M"} >= 15}${if_match ${exec date  +"%M"} < 20}${color}${endif}${endif}Q U A R T E R ${color1}D C
${if_match  ${exec date +"%M"} >= 20}${if_match ${exec date +"%M"} <  30}${color}${endif}${endif}T W E N T Y ${if_match ${exec date +"%M"}  >= 25}${if_match ${exec date +"%M"} <  30}${color}${endif}${else}${color1}${endif}${if_match ${exec date +"%M"}  >= 5}${if_match ${exec date +"%M"} < 10}${color}${endif}${endif}F  I V E ${color1}X
${if_match ${exec date +"%M"} >= 30}${if_match  ${exec date +"%M"} < 35}${color}${endif}${endif}H A L F ${color1}B  ${if_match ${exec date +"%M"} >= 10}${if_match ${exec date +"%M"}  < 15}${color}${endif}${endif}T E N ${color1}F T O
${else}${if_match  ${exec date +"%M"} >= 45}${if_match ${exec date +"%M"} <  50}${color}${endif}${endif}A ${color1}C ${if_match ${exec date +"%M"}  >= 45}${if_match ${exec date +"%M"} < 50}${color}${endif}${endif}Q  U A R T E R ${color1}D C
${if_match ${exec date +"%M"} >=  35}${if_match ${exec date +"%M"} < 45}${color}${endif}${endif}T W E N  T Y ${if_match ${exec date +"%M"} < 40}${if_match ${exec date +"%M"}  >= 35}${color}${endif}${else}${color1}${endif}${if_match ${exec date  +"%M"} >= 55}${color}${endif}F I V E ${color1}X
H A L F B  ${if_match ${exec date +"%M"} >= 50}${if_match ${exec date +"%M"}  < 55}${color}${endif}${endif}T E N ${color1}F ${color}T O${color1}
${endif}${if_match  ${exec date +"%M"} < 35}${if_match ${exec date +"%M"} >  5}${color}${endif}${endif}P A S T ${color1}E R U ${if_match ${exec date  +"%M"} < 35}${if_match ${exec date +"%I"} ==  9}${color}${else}${color1}${endif}N I N E
${if_match ${exec date  +"%I"} == 1}${color}${else}${color1}${endif}O N E ${if_match ${exec date  +"%I"} == 6}${color}${else}${color1}${endif}S I X ${if_match ${exec  date +"%I"} == 3}${color}${else}${color1}${endif}T H R E E
${if_match  ${exec date +"%I"} == 4}${color}${else}${color1}${endif}F O U R  ${if_match ${exec date +"%I"} == 5}${color}${else}${color1}${endif}F I V  E ${if_match ${exec date +"%I"} == 2}${color}${else}${color1}${endif}T W  O
${if_match ${exec date +"%I"} ==  8}${color}${else}${color1}${endif}E I G H T ${if_match ${exec date  +"%I"} == 11}${color}${else}${color1}${endif}E L E V E N
${if_match  ${exec date +"%I"} == 7}${color}${else}${color1}${endif}S E V E N  ${if_match ${exec date +"%I"} == 12}${color}${else}${color1}${endif}T W E  L V E
${if_match ${exec date +"%I"} ==  10}${color}${else}${color1}${endif}T E N ${else}${if_match ${exec date  +"%I"} == 8}${color}${else}${color1}${endif}N I N E
${if_match ${exec  date +"%I"} == 12}${color}${else}${color1}${endif}O N E ${if_match  ${exec date +"%I"} == 5}${color}${else}${color1}${endif}S I X ${if_match  ${exec date +"%I"} == 2}${color}${else}${color1}${endif}T H R E E
${if_match  ${exec date +"%I"} == 3}${color}${else}${color1}${endif}F O U R  ${if_match ${exec date +"%I"} == 4}${color}${else}${color1}${endif}F I V  E ${if_match ${exec date +"%I"} == 1}${color}${else}${color1}${endif}T W  O
${if_match ${exec date +"%I"} ==  7}${color}${else}${color1}${endif}E I G H T${if_match ${exec date +"%I"}  == 10}${color}${else}${color1}${endif} E L E V E N
${if_match ${exec  date +"%I"} == 6}${color}${else}${color1}${endif}S E V E N${if_match  ${exec date +"%I"} == 11}${color}${else}${color1}${endif} T W E L V E
${if_match  ${exec date +"%I"} == 9}${color}${else}${color1}${endif}T E N  ${endif}${color1}S E ${if_match ${exec date +"%M"} <  5}${color}${endif}O C L O C K

```[IMG]http://img684.imageshack.us/img684/9206/conkywordclock.png[/IMG]


i am trying to get this wordclock to work with conky.... any help is greatly appreciated :)

---

