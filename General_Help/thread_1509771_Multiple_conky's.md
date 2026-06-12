---
title: "Multiple conky's"
date: 2010-06-14
forum: General Help
---

### Post by greggc2006 on 2010-06-14
I am trying out conky for the first time and rather enjoying it. I have a small frustration though. I have a dual head setup and would like to have identical conky's showing on both monitors.

I have tried creating two .conkyrc's (.conkyrc1 & .conkyrc2) and then using:-

```
$ conky -c config1
$ conky -c config2
```

to launch them, this results in only one of the two conky's displaying. I did at first think that maybe they were on top of eachother, but one conkyrc is set bottom_left, the other bottom_right so they should not be right??

When I try to run them as above terminal shows:-

```
gregg@burt:~$ conky -c config1
Conky: invalid configuration file 'config1'

Conky: invalid num arg for top. Must be between 1 and 10.
Conky: invalid num arg for top. Must be between 1 and 10.
Conky: invalid num arg for top. Must be between 1 and 10.
Conky: invalid num arg for top. Must be between 1 and 10.
Conky: invalid num arg for top. Must be between 1 and 10.
Conky: invalid num arg for top. Must be between 1 and 10.
Conky: forked to background, pid is 7017
gregg@burt:~$ 
Conky: desktop window (1a00073) is subwindow of root window (15d)
Conky: window type - override
Conky: drawing to created window (0x4600001)
Conky: drawing to double buffer

gregg@burt:~$ conky -c config2
Conky: invalid configuration file 'config2'

Conky: invalid num arg for top. Must be between 1 and 10.
Conky: invalid num arg for top. Must be between 1 and 10.
Conky: invalid num arg for top. Must be between 1 and 10.
Conky: invalid num arg for top. Must be between 1 and 10.
Conky: invalid num arg for top. Must be between 1 and 10.
Conky: invalid num arg for top. Must be between 1 and 10.
Conky: forked to background, pid is 7025
gregg@burt:~$ 
Conky: desktop window (1a00073) is subwindow of root window (15d)
Conky: window type - override
Conky: drawing to created window (0x5000001)
Conky: drawing to double buffer

```  

I also tried:-

```
gregg@burt:~$ conky -c conkyrc1
Conky: invalid configuration file 'conkyrc1'

Conky: invalid num arg for top. Must be between 1 and 10.
Conky: invalid num arg for top. Must be between 1 and 10.
Conky: invalid num arg for top. Must be between 1 and 10.
Conky: invalid num arg for top. Must be between 1 and 10.
Conky: invalid num arg for top. Must be between 1 and 10.
Conky: invalid num arg for top. Must be between 1 and 10.
Conky: forked to background, pid is 6996
gregg@burt:~$ 
Conky: desktop window (1a00073) is subwindow of root window (15d)
Conky: window type - override
Conky: drawing to created window (0x4600001)
Conky: drawing to double buffer

gregg@burt:~$ conky -c conkyrc2
Conky: invalid configuration file 'conkyrc2'

Conky: invalid num arg for top. Must be between 1 and 10.
Conky: invalid num arg for top. Must be between 1 and 10.
Conky: invalid num arg for top. Must be between 1 and 10.
Conky: invalid num arg for top. Must be between 1 and 10.
Conky: invalid num arg for top. Must be between 1 and 10.
Conky: invalid num arg for top. Must be between 1 and 10.
Conky: forked to background, pid is 7008
gregg@burt:~$ 
Conky: desktop window (1a00073) is subwindow of root window (15d)
Conky: window type - override
Conky: drawing to created window (0x5000001)
Conky: drawing to double buffer

```

in case I was being a bit dim!!

both .conkyrc1 & .conkyrc2 are in my home dir, that is the right place for them?

===========================================================================

I do also have a second problem puzzling me, my config looks like:-
```
alignment bottom_left
background true
border_width 0
cpu_avg_samples 2
default_color grey
default_outline_color grey
default_shade_color grey
draw_borders no
draw_graph_borders no
draw_outline no
draw_shades no
use_xft yes
xftfont DejaVu Sans Mono:size=12
gap_x 700
gap_y 129
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_transparent 	yes
own_window_type 	override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes # Use double buffering (reduces flicker, may not work for everyone)
stippled_borders 0
update_interval 0.5
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no

TEXT
${font Sans:size=9:weight=bold}${color grey}SYSTEM ${hr 2}$color${font Sans:size=8:weight=bold}
${color grey}${time %A} - ${time %e} ${time %B} ${time %G} - ${time %H:%M}${alignr}
${color grey}Machine$color ${color grey}$nodename ${alignr}
${color grey}Uptime $color$uptime${alignr}
${color grey}Kernel$color  ${color grey}$kernel ${alignr}
# CPU
${font Sans:size=8:weight=bold}${color grey}CPU ${hr 2}$color
${color grey}${font}CPU: ${color red}${cpu cpu0}% $font${color}${alignr}FREQ: ${color red}${freq_g 1}Ghz$alignr ${color grey}
${color grey}${cpugraph cpu1 20,300 00ff0c 00ff0c }${color grey} 
#RAM
${font Sans:size=8:weight=bold}${color grey}MEMORY${hr 2}$color${font Sans:size=8:weight=bold}

${color grey}RAM: ${color red}$memperc%${alignr}${color grey}USED: ${color red}$mem/$memmax
${color grey}SWAP:$color $swapperc%${alignr}${color grey}USED: ${color red}$swap/$swapmax

#Processes
${font Sans:size=8:weight=bold}${color grey}PROCESSES${hr 2}$color${font Sans:size=8:weight=bold}
${color grey}Processes:$color $running_processes/$processes

${color grey} CPU%      MEM%     Name
${color red}${top cpu 01}      ${top mem 01}         ${top name 01}             
${color red}${top cpu 02}      ${top mem 02}         ${top name 02}             
${color red}${top cpu 03}      ${top mem 03}         ${top name 03}            
${color orange}${top cpu 04}      ${top mem 04}         ${top name 04}
${color orange}${top cpu 05}      ${top mem 05}         ${top name 05} 
${color orange}${top cpu 06}      ${top mem 06}         ${top name 06} 
${color yellow}${top cpu 07}      ${top mem 07}         ${top name 07} 
${color yellow}${top cpu 08}      ${top mem 08}         ${top name 08}             
${color yellow}${top cpu 09}      ${top mem 09}         ${top name 09}             
${color yellow}${top cpu 10}      ${top mem 10}         ${top name 10}            

#NETWORK
${font Sans:size=9:weight=bold}${color grey}NETWORK ${hr 2}$color${font Sans:size=8:weight=bold}
${color grey} DOWNLOAD                                  UPLOAD 
${downspeedgraph eth0 30,115 000000 00ff00} ${alignr}${upspeedgraph eth0 30,115 000000 ff0000}$color
```

Processes 8 & 9 do not appear in my conky, just blank space between 7 & 10?? Also, the swap %age displays 'No swap%'????

---

### Post by scouser73 on 2010-06-14
Although the thread I'm pointing you is for showing off Conky, I think you may get a better answer so here goes: 
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by muaythaimaster74 on 2010-06-14
I think the problem is in the naming of your files.  .conkyrc is only used for the initial conky file.  The other file can be called whatever you wish.  For example, I have 2 instances of conky running on my openbox setup.  The first is called with the simple command "conky".  It utilizes the .conkyrc file in my home directory.  The second is called with conky -c conkyclock... where conkyclock is the name of my second configuration file, also located in my home directory.

The result is the first instance showing in the top right... and the second in the top left.

It also looks like the number error is due to the 0 being placed before the number.  ie.. "top cpu 01" instead of just "top cpu 1".  

The swap error could be due to misconfigured swap... you should check your /etc/fstab against your blkid.  Issue the command "sudo blkid" and compare the UUID against the one in /etc/fstab.

---

### Post by stinkeye on 2010-06-14
For your start command use the full path
```
conky -c [COLOR="Purple"]/path/to your/conky[/COLOR]
```

---

### Post by greggc2006 on 2010-06-15
Thanks guy's, I'll try out renaming and using the full path and see what happens.

As far as the swap error goes, I'll check my fstab, but it is hand written from the output of blkid so should be fine?!?!?

I'll report back later, thanks again.

---

### Post by greggc2006 on 2010-06-15
All fixed up, excellent!!

It would appear that when I wrote my fstab I completely neglected to include a line for swap, doh!!

---

### Post by muaythaimaster74 on 2010-06-16
Glad ya got it sorted... have fun with conky!

---

