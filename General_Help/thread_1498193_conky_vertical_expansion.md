---
title: "conky vertical expansion"
date: 2010-05-31
forum: General Help
---

### Post by Forged on 2010-05-31
For some reason or another my conky bar has expanded to include another line.  It wasn't like that last night, it happened when I turned my computer on this morning. 

```

own_window                yes
own_window_class          Conky
own_window_type           panel
own_window_transparent    no
own_window_colour              303030
own_window_hints          undecorated,below,sticky,skip_taskbar,skip_pager
update_interval           1
double_buffer                  yes
alignment                 top_left
background                no
border_width              0
cpu_avg_samples           5
color1                            8f8f8f
color2                            e0e0e0
default_color             8f8f8f
default_outline_color     white
draw_borders              no
draw_graph_borders        no
draw_outline              no
draw_shades               no
use_xft                   yes
xftfont                   Sans:size=10
xftalpha                  1
gap_x                     0
gap_y                     0
minimum_size              1280 10
maximum_width             1280
net_avg_samples           2
no_buffers                yes
out_to_console            no
uppercase                 no
short_units               yes
pad_percents              1
text_buffer_size          512
override_utf8_locale      yes
mpd_host                  localhost
mpd_port                  6600
if_up_strictness          address


TEXT
  ${color1}Date: ${color2}${time %m/%d/%y}${color1}  Time: ${color2}${time %I:%M %P}${color1}${offset 50}Cpu: ${color2}${cpu}%${color1}${color1}  Ram: ${color2}${memperc}%  ${color1}Swap: ${color2}${swapperc}%   ${color1}/home: ${color2}${fs_used_perc /home}%${color1}    Battery: ${color2}${battery_percent BAT0}%${color2}${offset 30}${font ConkyWeather}${execi 3600 conkyForecast --location=USTX0057 --datatype=WF}${font}${offset 15}${color1}Temperature: ${color2}${execi 3600 conkyForecast --location=USTX0057 --datatype=HT --imperial} ${color1}${offset 30} Now Playing: ${execp conkyRhythmbox --template=~/conkyRhythmbox.template}

```

---

