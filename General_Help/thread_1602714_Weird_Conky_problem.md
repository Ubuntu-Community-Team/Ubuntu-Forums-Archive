---
title: "Weird Conky problem"
date: 2010-10-21
forum: General Help
---

### Post by medeshago on 2010-10-21
I can't use draw_shades in my conkyrc because it looks like this:
[IMG]http://imgur.com/7nBBN.png[/IMG]
If I change 'draw_shades' to 'no', it looks fine:
[IMG]http://imgur.com/f0X9Q.png[/IMG]
The weird part is that the other instance that I have of conky works fine, even though it doesn't differ from the one that behaves erratically.

Conkyrc that works:
```
# Conky configuration
background no
use_xft yes
xftfont Century Gothic:size=12
total_run_times 0
update_interval 1
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
stippled_borders 0
border_margin 0
border_width 0
default_color e0e0e0
default_shade_color 262729
default_outline_color 262729
alignment top_left
gap_x 1360
gap_y 980
override_utf8_locale yes
use_spacer yes
minimum_size 1280 25
maximum_width 1280 25
color1 snow
color2 floral white


TEXT
${alignc}${color1}Home: ${color2}${fs_free /home/edgardo}/${fs_size /home/edgardo}${color1}	/: ${color2}   ${fs_free /}/${fs_size /}
${color1}${alignr}${if_existing /media/IPOD/}Ipod: ${color2}${fs_free /media/IPOD/}/${fs_size /media/IPOD/}${endif}
```

Conkyrc that doesn't work:
```
# Conky configuration
background no
use_xft yes
xftfont Century Gothic:size=20
total_run_times 0
update_interval 2
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
stippled_borders 0
border_width 0
alignment top_left
gap_x 15
gap_y 730
override_utf8_locale yes
use_spacer yes
minimum_size 1360 25
maximum_width 1360 25
color1 snow
color2 floral white


TEXT
${color1}${alignc}     ${exec rhythmbox-client --no-start --print-playing-format %tt} ${font Century Gothic:size=14} ${exec rhythmbox-client --no-start --print-playing-format %aa}  ${color2}${font Century Gothic:size=8}${exec rhythmbox-client --no-start --print-playing-format %at}
```

---

