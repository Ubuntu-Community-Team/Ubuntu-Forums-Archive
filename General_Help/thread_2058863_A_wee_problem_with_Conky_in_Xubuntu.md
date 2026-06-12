---
title: "A wee problem with Conky in Xubuntu"
date: 2012-09-16
forum: General Help
---

### Post by M_Mynaardt on 2012-09-16
Hi There!

I use Xubuntu on my desktop computer.  What happens is that if I click the mouse pointer anywhere on the Conky display it just disappears.  I hadn't noticed this before only because the monitor is a nice big one and I've got my Conky display aligned on the top right.

Anyone know what might be the cause of this?

Here's my **.conkyrc** settings

```
#
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
# performance settings
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#
use_xft yes
xftalpha 1
update_interval 1.0
total_run_times 0
cpu_avg_samples 2
no_buffers yes
override_utf8_locale no
#
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
# window position
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#
alignment top_right
gap_x 40
gap_y 70
# 40 pixels from the right and 70 from the bottom
minimum_size 355 200
# minimum_size (width),(height)
#
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
# other window settings
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#
own_window yes
double_buffer yes
# double buffer to prevent flicker with own_window
own_window_argb_visual yes
# this needs to be set to "yes" in Xubuntu
own_window_type desktop
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
draw_borders no
border_width 8
border_inner_margin 10
# border settings, if needed
background no
own_window_colour 233d5d
# background window colour
#
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
# text settings
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#
font ubuntu:size=12
draw_shades yes
draw_outline yes
uppercase no
default_color d3d4d4
# A shade of silver that works nicely with most wallpapers
color0 007d79
# A shade of teal for file system and swap space bars
color1 5aed5a
# A shade of green for the memory graph and gauge
color2 e094e1
# A shade of purple for the CPU graph and gauge
color3 3dfbf5
# A shade of teal for the shortcuts legend
#
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
# graph settings
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#
draw_graph_borders yes
show_graph_range no
#

```

Thanks in advance!
):P

---

### Post by Habitual on 2012-09-16
Check out the other options for "own_window_type"
```
own_window_type
if own_window is yes, you may specify type normal,
desktop, dock, panel or override (default: normal).
```

---

### Post by M_Mynaardt on 2012-09-17
> **Habitual said:**
> Check out the other options for "own_window_type"
```
own_window_type
if own_window is yes, you may specify type normal,
desktop, dock, panel or override (default: normal).
```

Hi!

It was, indeed, the **own_window_type** attribute!  It had been set at normal, so I changed it to "desktop", and problem solved.  Coolness!

Thanks for that!
\\:D/

---

### Post by Habitual on 2012-09-17
You are very welcome.

---

