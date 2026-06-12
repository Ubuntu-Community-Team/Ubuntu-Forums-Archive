---
title: "Conky Disappears"
date: 2011-01-19
forum: General Help
---

### Post by GeissT on 2011-01-19
Hey,

So i have a keyboard shortcut (ALT+M) that i have set to minimize all active windows. Now when i set 'own_window yes' in the conkyrc file, it treats it as a window (what it is supposed to do) but when i use my shortcut it minimizes as well. Now in my docky bar, it does not appear.

I have tried setting it to 'own_window no' but then my icons disappear fron my desktop and i have to refresh the desktop every time conky updates (each on sec) this is an absolute nuisance.

I have the 'double_buffer yes' option set and that does stop the flickering that i was having but i still cant happily use conky. If you guys dont know a fix or workaround I will contact the conky developers.

Thanks in advance,

GeissT

---

### Post by Quackers on 2011-01-19
Please post your conkyrc file before the word TEXT (just the top half) in code tags

---

### Post by GeissT on 2011-01-19
Hey here is my conky config.

NOTE: I RECENTLY CHANGED OWN WINDOW TO NO TO SEE IF I COULD WORK IT OUT, BUT IT DIDNT WORK

```
# Conky, a system monitor, based on torsmo
#
# Any original torsmo code is licensed under the BSD license
#
# All code written since the fork of torsmo is licensed under the GPL
#
# Please see COPYING for details
#
# Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
# Copyright (c) 2005-2010 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
# All rights reserved.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

alignment top_right
background no
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
use_xft yes
xftfont DejaVu Sans Mono:size=12
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
double_buffer yes
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window no
own_window_transparent yes
own_window_class Conky
own_window_type root
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no
```

---

### Post by Vaphell on 2011-01-19
[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

look at own_window_type
desktop or override should make conky resistant to 'minimize all windows'

---

### Post by Quackers on 2011-01-19
The only differences between yours and mine (apart from colour/shade) is that I have
own_window yes and yours is own_window no
and I have 
own_window_type override and you have own_window-type root
You can see if that makes a difference.

---

### Post by GeissT on 2011-01-19
Thank you so much Quackers. changing to own window yes. And the type to override works a treat. Thanks soo much.

Thanks also to Vaphell, ill take a look at that resource in the future.

---

### Post by Quackers on 2011-01-19
Very niiiiiiiice :-)

---

### Post by MiKOTRON on 2011-01-19
> **Vaphell said:**
> [http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

look at own_window_type
desktop or override should make conky resistant to 'minimize all windows'

I've been having this same problem.  The things you learn when you RTFM.  Who'd of thunk?  So yeah, thank you!  :)

---

