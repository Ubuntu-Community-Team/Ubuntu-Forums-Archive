---
title: "Wrong RAM reading from system monitor?"
date: 2010-03-14
forum: General Help
---

### Post by josepaul on 2010-03-14
OK, straight to the point, look at the screen shot, conky shows I am using lots of RAM when System Monitor shows otherwise but ```
free -m
```
gives the output
```
             total       used       free     shared    buffers     cached
Mem:           749        626        122          0        107        239
-/+ buffers/cache:        279        469
Swap:          713          0        713

```
This shows that the system isn't using just ~287MB RAM

This is my .conkyrc file-

```
use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes${color ffffff}${font StyleBats:size=16}P${font}
uppercase no
color1 F8DF58
update_interval 1.0



TEXT
   ${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth0}
   ${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth0} 

   ${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth0}
   ${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth0}

   ${color ffffff}${font StyleBats:size=16}A${font}  CPU: ${cpu cpu0}% ${cpubar cpu0}

   ${color ffffff}${font StyleBats:size=16}I${font}  RAM: ${memperc}% ${membar}
  
   ${color ffffff}${font StyleBats:size=16}J${font} Disk: ${fs_used_perc}% ${fs_bar}
   
   ${color ffffff}${font StyleBats:size=16}J${font} Swap: ${swapperc}% ${swapbar} 
   
   ${color ffffff}${font StyleBats:size=18}P${font}  CPU Temp: ${execi 3 sensors | grep "temp2:" | cut --characters 15-16} °C

   ${font StyleBats:size=18}P${font}  Uptime:  ${uptime}


 ${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %H:%M}

```

---

### Post by dcstar on 2010-03-14
> **josepaul said:**
> OK, straight to the point, look at the screen shot, conky shows I am using lots of RAM when System Monitor shows otherwise but ```
free -m
```
gives the output
```
             total       used       free     shared    buffers     cached
Mem:           749        626        122          0        107        239
-/+ buffers/cache:       ** 279 **       469
Swap:          713          0        713

```
This shows that the system isn't using just ~287MB RAM
.........

Yes it does, just as your System Monitor reports.

And 626 used out of 749 is the 84% that Conky reports, so everything is working exactly as it should.

---

### Post by josepaul on 2010-03-14
> **dcstar said:**
> Yes it does, just as your System Monitor reports.

And 626 used out of 749 is the 84% that Conky reports, so everything is working exactly as it should.

Sorry you lost me, conky shows that I'm using 84% whilst System monitor reports that I'm using 38.3%, are these referring to 2 different values?

---

### Post by uRock on 2010-03-14
I believe that System Monitor doesn't show cached memory. I could be wrong.

---

### Post by josepaul on 2010-03-14
Oh right I get it, thanks for the replies guys :)

---

