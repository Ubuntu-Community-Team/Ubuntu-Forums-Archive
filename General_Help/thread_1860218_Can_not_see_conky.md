---
title: "Can not see conky"
date: 2011-10-14
forum: General Help
---

### Post by papaapa on 2011-10-14
Today i installed Ubuntu 11.10 and i use it with Gnome-shell. I can start the conky properly (without any eorror) from terminal but i could not see the conky on the desktop. The same conky works properly on my Ubuntu 11.04.
My conky's code is this:

```
font Sans:size=10
use_xft yes
update_interval 60
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
default_color white
alignment top_left
gap_x 200
gap_y 250
cpu_avg_samples 2
override_utf8_locale no

TEXT
${font Ubuntu:size=20}${time %H:%M %A %d %B %Y}
```

---

### Post by papaapa on 2011-10-15
Can somebody help me please? :(

---

### Post by Pcmechanic on 2011-10-15
Hi

I was having the same problem but i think I've solved it (this works for me)

Open the conky config and find :

own_window_type
own_window_hints

Then change the values to 

own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

Save the config file and it should appear

---

### Post by papaapa on 2011-10-15
Pcmechanic solved. Thank you :)

---

