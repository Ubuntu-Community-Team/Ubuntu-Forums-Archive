---
title: "could anyone help with conky setup?"
date: 2009-10-01
forum: General Help
---

### Post by Guy Sibley on 2009-10-01
I have a few questions about conky.
So I downloaded conky, and found a good setup online, however the network monitor is not doing anything, which I find lame.  How do I fix this? Also, I have seen pics of conky with weather, again how? I guess I just don't understand how this program works, or how to install add ons like this. Does anyone know of a good set of instructions, or just some general info on how to deal with these problems?
Thanks a lot
Guy.

---

### Post by trstncmpbll on 2009-10-01
so for internet are you using wireless or a eht? go to your script and just change it to what you use, for example my computer reads my wireless as eth1. i learned it by messing around with it a lot and just really looking at scripts and trying to understand them

${color green}Wireless$color
${tab 20}IP Local ${alignr}${addr eth1}
${tab 20}IP Public ${alignr}${execi 5 ~/.scripts/ip.sh}
${tab 20}AP ESSID: ${wireless_essid eth1} ${alignr}AP Bitrate: ${wireless_bitrate eth1}
${color green}Down: ${color green}${downspeedf eth1}k/s ${color green}${alignr}Up: ${color green}${upspeedf eth1}k/s$color
${color green}${downspeedgraph eth1 9,125 000000 000000} ${alignr}${color green}${upspeedgraph eth1 9,125 000000 000000}$color
${tab 20}Total: ${totaldown eth1}          Total: ${totalup eth1}

so all those eth1 or whatever they may be in your script change em

[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)
check that out for basically a list of codes

---

### Post by Guy Sibley on 2009-10-01
thanks.

---

### Post by trstncmpbll on 2009-10-01
also anything inside a ${} is a command and doesnt show on conky. so anything outside of it you could edit the text etc

---

### Post by Guy Sibley on 2009-10-01
The other odd thing was when I added conky to my startup programs it had a border around it instead of looking like part of my desktop. I am using compiz but that didn't seem to matter before. Thanks again for your help.

---

### Post by trstncmpbll on 2009-10-01
so on most premade conky setups the top half is how your conky will look and the second half is whats in your conky 

background yes
use_xft no
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 280 5
maximum_width 250
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color green
default_shade_color green
default_outline_color green
alignment bottom_left
gap_x 10
gap_y 10
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
use_spacer yes

anything relating to borders or outlines, but some outlines are for graphs. just change it to no. and the gap x,y is your conkys location also turn on double buffer that reduces flicker

heres what my desktop looks like
[IMG]http://img.photobucket.com/albums/v610/trstncmpbll/myconky.jpg[/IMG]

---

### Post by dcclabough on 2009-10-04
> The other odd thing was when I added conky to my startup programs it had a border around it instead of looking like part of my desktop. I am using compiz but that didn't seem to matter before. Thanks again for your help. 
3 Days Ago 12:29 PM

the problem is that compiz is apllying its window settings to conky because it loads before compiz does its thing... all you need to do is add a file somewhere (probably user folder is best)

```
sudo gedit ~/.conky_start.sh
```

save and close file,
then add:

```
#!/bin/bash
sleep 12 && conky;
```

the sleep 12 just tells conky to wait 12 seconds before starting so compiz doesnt try to do funny stuff to the window... (you can experiment with lower sleep times, but 12 is about my limit)

then:

```
sudo chmod a+x ~/.conky_start.sh
```

this makes the file executable.

then just change the startup app entry to point to /home/[user]/.conky_start.sh
and you're all good

---

