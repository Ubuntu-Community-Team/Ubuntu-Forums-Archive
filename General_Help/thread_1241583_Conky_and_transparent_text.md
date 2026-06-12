---
title: "Conky and transparent text"
date: 2009-08-16
forum: General Help
---

### Post by HiImTye on 2009-08-16
hi, I was wondering if it is possible to make an individual section of text transparent in conky, other than just with the xft font. the reason I'm asking is I'm making a clock config file and I want just the clock line to be transparent (and blend together). As it is right now, only the 'hour' is transparent, the rest of the line uses a different font size which ignores the xft setting. here's what I have

```
#position
alignment top_left
gap_x 370
gap_y 450

#appearance
background no
draw_shades no
draw_outline no

#fonts
use_xft yes
xftfont Bitstream Vera Sans Mono:size=50
xftalpha 0.5

#system stuff
update_interval 1.0
total_run_times 0
double_buffer yes
no_buffers yes
override_utf8_locale no

TEXT
${color 0000FF}${offset 50}${voffset -10}${font Bitstream Vera Sans Mono:size=40}${time %M}${offset -20}${voffset 10}${color 00FFFF}${font Bitstream Vera Sans Mono:size=20}${time %S}${font}${offset -130}${voffset -40}${color 0080FF}${time %H}${font Palladio Uralic:size=8.3}
${color 00FF80}${time %A}, ${time %B} ${time %e} ${time %Y}
```

---

