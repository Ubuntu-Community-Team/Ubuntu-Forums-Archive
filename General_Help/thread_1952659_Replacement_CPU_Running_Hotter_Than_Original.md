---
title: "Replacement CPU Running Hotter Than Original"
date: 2012-04-04
forum: General Help
---

### Post by klingonklingoff on 2012-04-04
Hey guys im putting together a barebones desktop. Have AMD phenom II x6 1045T. and gigabyte mobo. I ordered the kit in mail. Put it together and it was running at 35 C. This was with bios only and no OS at all. Long story short had to send back the CPU and mobo as defective. Installed same brand and model cpu and mobo. But it now runs at about 39 C in bios. I dont remember if it was at 39C before i installed Ubuntu 11.10 64 bit or after as im not quite sure which. Now with ubuntu it runs at about 42 C and when turning on virtual box its running up to 48 C. I know this is under max temps but the base temp was at 35 C with previous CPU compared to 39C with replacement CPU . Should i worry about the difference or is it not enough to make any difference? Also the replacement CPU had a heat sink locking device to the Mobo/CPU that looks cheaper than the first one. Any ideas appreciated. Thanks

---

### Post by QIII on 2012-04-04
You need to worry.

That Phenom II x6 will flame out at 60 degrees.  If you are getting in the 40s under so light a load, you are in trouble.  Especially since the on die thermistor reads 8 - 10 low.

Are you sure you are even getting the CPU temp or the socket temp.

You have a serious problem with your cooling solution.  I have a Noctua NH-D14 on my 1100 T Black and, adjusting up by 10 degrees, I run at 29 idle and I've never been above 47 at 100% load.

---

### Post by klingonklingoff on 2012-04-04
Maybe i should be more clear but im running VirtualBOX from oracle as a VM with windows vista 64 bit simultaneously watcing silverlight videos. I just got 2X 120mm fans today and will replace the POS 80mm fans that i currently have. One on the side over cpu and one in back under PSU. Thanks. About the temps im running psensor on linux and they are listed as temp1 temp2 and temp 3 and the one that states for pci actually reads 6000 degrees

---

### Post by QIII on 2012-04-04
I still don't think that should generate such a high load that you should be getting those kind of temperatures.

With all of that running, what is your CPU load?

Are you using the woefully inadequate HSF you got with the CPU?  That is a death sentence.

Edit:  those temps are mobo temps and one is the socket.  The socket won't give you the true CPU temp (neither does the on-die thermistor, even rounded up.  AMD has some magical "reference temperature" deal), but is probably at least 5 degrees lower than the actual CPU.

---

### Post by klingonklingoff on 2012-04-04
Yes I am. What do u suggest...brand and model or even type. I dont have any 80mm fans yet that have 3 pins as stock Only 4 pin molex right now. Im going to blow the 120MM fan i just got over the cpu for tonight and then get a good 80 mm with 3 pin. Also the manual states that any aftermarket heat sinks will void my warranty. does this go for the fan too?. Is this true or should i just get better cooler. Actually im interested in cooller master 212 plus. will this work? my current 80mm fans cost 99 cents. I think i should have went with bettter ones as this can kill my machine.

---

### Post by klingonklingoff on 2012-04-04
Another thing that comes to mind is that ubuntu 11.10 in 3d freezes up requireing rebbot for some reason especially playing u tube. while i just switched to 2d (did not realize it had this option till other day) and have not froze up since. Is this temp related?

---

### Post by QIII on 2012-04-04
An inadequate HSF will destroy your CPU and if you RMA it they may say it's your fault anyway.

The Hyper 212+ is the very least I would go.  Better for an x4 maybe.

I don't want to tell you how to spend your money.  That's not mine to say.  Do some research and read some reviews so you can make an informed decision on cost/performance.

But I will tell you this in general:  Never skimp on cooling.  (Or PSUs, for that matter.)

Also, be careful how much thermal compound you use.  Too much is often worse than too little.

---

### Post by gordintoronto on 2012-04-05
I highly recommend lm-sensors and conky to keep an eye on temperatures.

There's probably some extraneous stuff in here, but it works:

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar,skip_pager
background yes
own_window_transparent yes

# If own_window is yes, you may use type normal, desktop or overide
# own_window_type normal

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Don't count buffers as used memory
no_buffers

use_spacer right
use_xft yes
xftfont Terminus:size=11
xftalpha 1

# Update interval in seconds
update_interval 2.0

# Size of window
minimum_size 200 5
maximum_width 400

# Draw shades?
draw_shades no

# Text stuff
draw_outline yes
draw_borders yes
draw_graph_borders yes
uppercase no

# border margins
border_outer_margin 2
stippled_borders 0
border_width 1

# Default colors and also border colors
default_color FFFFFF
default_shade_color 5D009C
default_outline_color 000000

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 5
gap_y 0

override_utf8_locale no

# stuff after 'TEXT' will be formatted on screen
TEXT
Gord's Minty Cinnamon

${color #A548CC}Uptime:${color}    ${uptime}
${color #A548CC}Kernel:${color}      ${exec uname -r|cut -b1-8}
${color #A548CC}CPU Temp:${color}         ${hwmon temp 1}C
${color #A548CC}Drive Temp:${color}       ${hddtemp}C
${color #A548CC}Video Temp:${color}       ${nvidia temp}C
${color #A548CC}Chipset Temp:${color}    ${execi 8 sensors | grep temp1 | grep low| cut -c16-17 | sed '/^$/d'} C

${color #A548CC}Phenom II:${color}         ${freq_g}GHz  (${cpu}%)

${color #A548CC}MEM:   ${membar 3,100}${alignr}(${memperc}%)
${color}${mem} / ${memmax}  
${color #A548CC}SWAP: ${swapbar 3,100}${alignr}(${swapperc}%)
${color}${swap} / ${swapmax}

${color #A548CC}ROOT:  ${fs_bar 3,100 /}${alignr}(${fs_free_perc /}%)
${color}${fs_used /}/ ${fs_size /}
${color #A548CC}HOME: ${fs_bar 3,100 /home}${alignr}(${fs_free_perc /home}%)
${color}${fs_used /home}/ ${fs_size /home}
```

---

### Post by QIII on 2012-04-05
Geez!  I waited to give a guy some conky suggestions until he had at least 17 beans! ;)

---

### Post by Mark Phelps on 2012-04-05
A good site to check out for HSF reviews is HardOCP.  They regularly do tests on several HSFs, including seeing how well the work when the CPU is overclocked.

---

### Post by Cheesemill on 2012-04-05
[http://www.bit-tech.net](http://www.bit-tech.net) also has good reviews.

---

### Post by xyzzyman on 2012-04-07
Properly cleaning the CPU & heatsink, and properly applying a good thermal compound is also very important. I've replaced the compound on new OEM desktops and seen 5-10degree drops just because of the difference in quality of compound and proper application. Acer is horrible for overdoing their cheap compound.

---

