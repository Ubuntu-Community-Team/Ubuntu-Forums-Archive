---
title: "Conky Cuts Off at the Bottom"
date: 2011-10-05
forum: General Help
---

### Post by murderd2death on 2011-10-05
so i got conky running but at a certain point it cuts off whatever script i have running at the bottom. I have as much script running as i can at the moment, one more line and its cut off. I have looked at other threads and tried codes like ```

text_buffer_size 512
```

to no avail. Please help. Here is my .conkyrc

```
minimum_size 182 700
background yes
font Arial:size=10
xftfont Arial:size=10
use_xft yes
xftalpha 0.1
update_interval .6
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 280 9
maximum_width 220
default_color white
default_shade_color black
default_outline_color white
alignment top_right
gap_x 2
gap_y 30
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

text_buffer_size 512
TEXT
${font Arial:style=Boldixelsize=42}${alignc}${time %H:%M:%S}${font Arial:size=8.5}
SYSTEM ${hr }

Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg
Battery ${battery_time BAT0} ${alignr}(${battery BAT0})
${battery_bar 4 BAT0}

File System 
${fs_used /}/${fs_size /}${alignr}${fs_bar 5,120 /}

CPU 1                  $alignr CPU 2
${cpugraph cpu1 25,100 0077ff eeeeee} $alignr${cpugraph cpu2 25,100 0077ff eeeeee}
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}
${color white}SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Network ${hr 2}
${execi 30 rm -f .conky_eth0; ifconfig -s | grep eth0 > /dev/null && ifconfig -a eth0 | grep 'inet addr:' > /dev/null && touch .conky_eth0}${execi 30 rm -f .conky_eth1; ifconfig -s | grep eth1 > /dev/null && ifconfig -a eth1 | grep 'inet addr:' > /dev/null && touch .conky_eth1}${if_existing /home/username/.conky_eth0}IP (eth0):$alignr${addr eth0}
Down: ${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 20,100 444444 eeeeee} ${alignr}${upspeedgraph eth0 20,80 444444 eeeeee}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${endif}${if_existing /home/username/.conky_eth1}IP (eth1):$alignr${addr eth1}
Down: ${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s
${downspeedgraph eth1 20,100 0077ff eeeeee} ${alignr}${upspeedgraph eth1 20,80 0077ff eeeeee}$color
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
${hr 2}
CPU Usage    ${alignr}     PID CPU% MEM%
${top name 1} ${alignr}${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} ${alignr}${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} ${alignr}${top pid 3} ${top cpu 3} ${top mem 3}

Mem Usage
${top_mem name 1} ${alignr}${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${top_mem name 2} ${alignr}${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${top_mem name 3} ${alignr}${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

Rhythmbox ${hr 2}
Artist: ${exec rhythmbox-client --no-start --print-playing-format %aa}
Album: ${exec rhythmbox-client --no-start --print-playing-format %at}
Track: ${exec rhythmbox-client --no-start --print-playing-format %tt} 
```

---

### Post by TeoBigusGeekus on 2011-10-05
> minimum_size 182 700
...
minimum_size 280 9
You have two minimum size lines.
Try deleting one and keeping
```
minimum_size 280 700
```
Change 700 to 1000 if necessary.

---

### Post by InterNut on 2011-10-05
I see you have 2 instances of "minimum_size", that might have something to do with it?

---

### Post by InterNut on 2011-10-05
darn, to late :)

---

### Post by murderd2death on 2011-10-06
> **TeoBigusGeekus said:**
> You have two minimum size lines.
Try deleting one and keeping
```
minimum_size 280 700
```Change 700 to 1000 if necessary.

no luck, i changeg to to 700 and back and took away the other line of code, and it gets cut off at the bottom. I put some extra mem usage scripts to show it.

```
minimum_size 182 700
background yes
font Arial:size=10
xftfont Arial:size=10
use_xft yes
xftalpha 0.1
update_interval .6
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
maximum_width 220
default_color white
default_shade_color black
default_outline_color white
alignment top_right
gap_x 2
gap_y 30
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

text_buffer_size 512
TEXT
${font Arial:style=Boldixelsize=42}${alignc}${time %H:%M:%S}${font Arial:size=8.5}
SYSTEM ${hr }

Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg
Battery ${battery_time BAT0} ${alignr}(${battery BAT0})
${battery_bar 4 BAT0}

File System 
${fs_used /}/${fs_size /}${alignr}${fs_bar 5,120 /}

CPU 1                  $alignr CPU 2
${cpugraph cpu1 25,100 0077ff eeeeee} $alignr${cpugraph cpu2 25,100 0077ff eeeeee}
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}
${color white}SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Network ${hr 2}
${execi 30 rm -f .conky_eth0; ifconfig -s | grep eth0 > /dev/null && ifconfig -a eth0 | grep 'inet addr:' > /dev/null && touch .conky_eth0}${execi 30 rm -f .conky_eth1; ifconfig -s | grep eth1 > /dev/null && ifconfig -a eth1 | grep 'inet addr:' > /dev/null && touch .conky_eth1}${if_existing /home/username/.conky_eth0}IP (eth0):$alignr${addr eth0}
Down: ${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 20,100 444444 eeeeee} ${alignr}${upspeedgraph eth0 20,80 444444 eeeeee}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${endif}${if_existing /home/username/.conky_eth1}IP (eth1):$alignr${addr eth1}
Down: ${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s
${downspeedgraph eth1 20,100 0077ff eeeeee} ${alignr}${upspeedgraph eth1 20,80 0077ff eeeeee}$color
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
${hr 2}
CPU Usage    ${alignr}     PID CPU% MEM%
${top name 1} ${alignr}${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} ${alignr}${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} ${alignr}${top pid 3} ${top cpu 3} ${top mem 3}

Mem Usage
${top_mem name 1} ${alignr}${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${top_mem name 2} ${alignr}${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${top_mem name 3} ${alignr}${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
${top_mem name 3} ${alignr}${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
${top_mem name 3} ${alignr}${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
${top_mem name 3} ${alignr}${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}


Rhythmbox ${hr 2}
Artist: ${exec rhythmbox-client --no-start --print-playing-format %aa}
Album: ${exec rhythmbox-client --no-start --print-playing-format %at}
Track: ${exec rhythmbox-client --no-start --print-playing-format %tt} 
```

---

### Post by TeoBigusGeekus on 2011-10-06
No idea why this is happening.
I used your exact same script and everything was ok.
[[IMG]http://i.imgur.com/NkXw4s.jpg[/IMG]]("http://i.imgur.com/NkXw4.jpg")
I even added extra blank lines to increase its size and it still worked alright.
[[IMG]http://i.imgur.com/5Guc6s.jpg[/IMG]]("http://i.imgur.com/5Guc6.jpg")
The only thing I can think off is the conky version.
Mine is conky 1.8.1-3, what's yours?

---

### Post by Quackers on 2011-10-06
Does anything change if you try ```
text_buffer_size 1024
```

A text_buffer_size which is too small can cause conky's output to be truncated.

---

### Post by BoogeyOfTheMan on 2012-07-12
I would just like to add that after you make said changes, killall conky and restart it. My changes didnt take until I did that.

---

### Post by jmfal on 2012-07-12
YOU can do killall conky or double click save and conky should restart

---

