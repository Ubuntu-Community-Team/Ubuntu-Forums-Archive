---
title: "Conky font problem"
date: 2010-09-01
forum: General Help
---

### Post by dmillerw on 2010-09-01
If there's a better spot to place this, sorry I didn't notice it

.conkyrc
```
background no
font DejaVu Sans:size=8
#xftfont DejaVu Sans:size=8
use_xft yes
xftalpha 0.9
update_interval 3.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 185 5
maximum_width 185
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color black
alignment top_right
gap_x 13
gap_y 33
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase yes # set to yes if you want all text to be in uppercase
draw_shades yes
lua_load ~/.scripts/draw_bg.lua
lua_draw_hook_pre draw_bg

TEXT
${color aaaaaa} $alignr ${upspeed eth0} / ${downspeed eth0}
${color aaaaaa} $alignr ${execi 3600 wget -O - http://ip.tupeux.com | tail} / ${addr eth0}

${color aaaaaa} ${alignr}${fs_free /} / ${fs_size /}

${font ConkyWeather:size=36} ${execpi 1800 conkyForecast --location=USOR0118 --imperial --template=/usr/share/conkyforecast/example/conkyForecast.template}

${color white} $alignr TODO
${color aaaaaa} $alignr ${execi 30 cat ~/.scripts/todo.txt | fold -w40 }
```

However it outputs like this...

[IMG]http://img837.imageshack.us/img837/8893/selection006m.png[/IMG]

...how can I make it only apply the font to a particular section

---

### Post by DemonBob on 2010-09-01
> **dmillerw said:**
> If there's a better spot to place this, sorry I didn't notice it

.conkyrc
```
background no
font DejaVu Sans:size=8
#xftfont DejaVu Sans:size=8
use_xft yes
xftalpha 0.9
update_interval 3.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 185 5
maximum_width 185
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color black
alignment top_right
gap_x 13
gap_y 33
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase yes # set to yes if you want all text to be in uppercase
draw_shades yes
lua_load ~/.scripts/draw_bg.lua
lua_draw_hook_pre draw_bg

TEXT
${color aaaaaa} $alignr ${upspeed eth0} / ${downspeed eth0}
${color aaaaaa} $alignr ${execi 3600 wget -O - http://ip.tupeux.com | tail} / ${addr eth0}

${color aaaaaa} ${alignr}${fs_free /} / ${fs_size /}

${font ConkyWeather:size=36} ${execpi 1800 conkyForecast --location=USOR0118 --imperial --template=/usr/share/conkyforecast/example/conkyForecast.template}

${color white} $alignr TODO
${color aaaaaa} $alignr ${execi 30 cat ~/.scripts/todo.txt | fold -w40 }
```

However it outputs like this...

[IMG]http://img837.imageshack.us/img837/8893/selection006m.png[/IMG]

...how can I make it only apply the font to a particular section

Change this: 

```
${font ConkyWeather:size=36} ${execpi 1800 conkyForecast --location=USOR0118 --imperial --template=/usr/share/conkyforecast/example/conkyForecast.template}
```

To this: 

```
${font ConkyWeather:size=36} ${execpi 1800 conkyForecast --location=USOR0118 --imperial --template=/usr/share/conkyforecast/example/conkyForecast.template}${font}
```


If you don't add the closing ${font} tag, then font carries on to the rest of the document.

---

