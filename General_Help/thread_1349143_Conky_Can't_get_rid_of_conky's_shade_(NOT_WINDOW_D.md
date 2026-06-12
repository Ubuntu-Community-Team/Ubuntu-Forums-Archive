---
title: "Conky: Can't get rid of conky's shade (NOT WINDOW DECORATION)"
date: 2009-12-08
forum: General Help
---

### Post by rfkrocktk on 2009-12-08
I can't seem to get rid of a particularly annoying feature of conky. When I try to draw outlines around the text using the script below, I get ugly "drop shadows" which are really conky's shade feature. I can't figure this one out. I've looked through the entire manual and can't find an option to just outline the text without adding the shade. I've attached a screenshot showing how weird this looks as well as my .conkyrc file to see if anyone can help me spot the error. I do want the text outline, I just don't want the artificial drop shadow or shade that conky is drawing. 

NOTE: This is NOT about window decoration drop shadow. I already got rid of that via compizconfig-settings-manager. 

.conkyrc
```
background no
use_xft yes
update_interval 0.5
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
alignment bottom_right
gap_x 5
gap_y 5
draw_outline yes
draw_borders no
draw_shades no
no_buffers no
border_margin 0
border_width 0

TEXT

${font :size=30}${alignr}${time %I:%M}${font :size=8}
${time %A, %B %d, %Y}
```

---

### Post by eogahn on 2009-12-17
I have the exact same problem, its very strange, I've looked online and other people have it working properly, but I can't figure out the .conkyrc command they use.

---

### Post by rfkrocktk on 2009-12-18
I figured it out some days ago. I recommend that you clear everything out of your .conkyrc file and rewrite it from scratch. Ordering of certain tags will cause this strange problem.

---

### Post by martingwb on 2012-05-17
Hi,
I just ran into the same problem with conky in 12.04. When usging ```
draw_outline yes
```

I solved this by starting the TEXT section with a line for formatting the text:

```
...
draw_shades no
draw_outline yes
#draw_borders no
font Monospace:size=8:weight=normal
#uppercase no

TEXT
#the following line is necessary to not display shades
${font Arial:bold:size=8}
...
```

---

