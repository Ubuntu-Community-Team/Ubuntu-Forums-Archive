---
title: "Temperature of CPU in conky"
date: 2009-10-03
forum: General Help
---

### Post by sopadeajo on 2009-10-03
Trying to get temperature of CPU in conky, but the variable acpitemp (shows 0) or adt746xcpu do not seem to work. I do not know if i installed all the necessary programs though. How to make it work ?

---

### Post by sopadeajo on 2009-10-03
[IMG]http://img23.imageshack.us/img23/8749/18151802.png[/IMG]

Anybody knows why pulseaudio is taking 1 % CPU usage while i was listening to nothing?
[IMG]http://yfrog.com/0n18151802p[/IMG]
[IMG]http://yfrog.com/0n18151802p[/IMG]

---

### Post by sopadeajo on 2009-10-04
Nobody has any interest in Conky here ?

---

### Post by ikacer on 2009-10-04
What version of conky are you using? Also, it would be helpful if you posted your .conkyrc.


here are a couple links you should check out:

Conky documentation:
[http://conky.sourceforge.net/documentation.html]("http://conky.sourceforge.net/documentation.html")

and here is a list of variables:
[http://conky.sourceforge.net/variables.html]("http://conky.sourceforge.net/variables.html")

---

### Post by sopadeajo on 2009-10-04
Here is the conky configuration:


alignment bottom_left
background yes
border_width 1
cpu_avg_samples 2
default_color pink
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
font 9x15
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
own_window yes
own_window_class Conky
own_window_type normal
stippled_borders 0
update_interval 3.0
uppercase no
use_spacer no
show_graph_scale no
show_graph_range no

TEXT
${scroll 16 $nodename - $sysname $kernel on $machine | }
$hr
${color grey}Uptime:$color $uptime
${color grey}Frequency (in GHz):$color $freq_g
${color grey}Temperature (in C):$color $acpitemp
${color grey}Disk:$color $diskio
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$hr
${color grey}File systems:
 / $color${fs_free /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking:
Up:$color ${upspeed eth1} kB/s${color grey} - Down:$color ${downspeed eth1} kB/s
$hr
${color grey}Name                  PID   CPU%   MEM%
${color lightgreen} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color lightblue} ${top name 5} ${top pid 5} ${top cpu 5} ${top mem 5}

---

### Post by ikacer on 2009-10-04
I don't see anything wrong with your .conkyrc. Maybe your problem is that you just cant detect the cpu temp.

Make sure you have lm-sensors installed.
```
sudo apt-get install lm-sensors
```
You also need to configure your sensors:
```
sudo sensors-detect
```
at then end of this program it will offer to update /etc/modules which you should answer yes to (it just appends a line of text to /ect/modules)
Then restart you computer and hopefully acpitemp will work.

---

### Post by sopadeajo on 2009-10-04
> **ikacer said:**
> I don't see anything wrong with your .conkyrc. Maybe your problem is that you just cant detect the cpu temp.

Make sure you have lm-sensors installed.
```
sudo apt-get install lm-sensors
```You also need to configure your sensors:
```
sudo sensors-detect
```at then end of this program it will offer to update /etc/modules which you should answer yes to (it just appends a line of text to /ect/modules)
Then restart you computer and hopefully acpitemp will work.

I have done step by step all of it, then restarted and finally all works but not ${acpitemp} variable. I do not know if it is because i am on Jaunty or because it only works on laptops (i am on a desktop).

---

### Post by ikacer on 2009-10-05
> **sopadeajo said:**
> I have done step by step all of it, then restarted and finally all works but not ${acpitemp} variable. I do not know if it is because i am on Jaunty or because it only works on laptops (i am on a desktop).

It works fine for me in Jaunty and I think it should work on desktops as well, so I don't know what else to suggest.

---

### Post by sopadeajo on 2009-10-05
I have added to panel the Hardware Sensors Monitor  applet and they tell me CPU temperature as well of 2 more temperatures. I think the problem is the variable 'acpitemp' in Conky which is not the correct one or else there is an unknown bug somewhere.

---

### Post by ikacer on 2009-10-05
Well then, here is a possible work-around using the execi variable in conky:
If you have a way to output the cpu temperature in the terminal, you can the pipe it to grep, then to cut to get just the part you want. there is a program called "acpi" in the reps that can list acpi sensor outputs. So, I could get the the acpi temperature by:
```
${execi 2 acpi -V | grep "Thermal 0" | cut -c21-24}
```
You will probably have to change the values for cut, and maybe grep to get it to work on your system. I do a similar thing to get the GPU temperature in my .conkyrc. I have an nvidia card so I just use:
```
${execi 2 nvidia-settings -query GPUCoreTemp | grep Attribute | cut -c50-51}
```

I've also attached my .conkyrc and a screenshot. Maybe it will be helpful as a reference.

EDIT: here is also a useful thread to check out: [http://ubuntuforums.org/showthread.php?t=281865]("http://ubuntuforums.org/showthread.php?t=281865")

---

### Post by yeeeev on 2009-10-05
Another option is:
${execi 120 cat /proc/acpi/thermal_zone/THM/temperature | awk '{print $2 " "$3}'}

---

### Post by Bigneil on 2009-10-05
what is conky ?

---

### Post by sopadeajo on 2009-10-05
> **Bigneil said:**
> what is conky ?



This is what we are all talking about and would be delighted to know.



Edited:  


A software device unable to detect the temperature.

---

### Post by ikacer on 2009-10-05
> **Bigneil said:**
> what is conky ?

[http://en.wikipedia.org/wiki/Conky_%28software%29]("http://en.wikipedia.org/wiki/Conky_%28software%29")

---

### Post by zekonology on 2009-10-19
nice!!! :guitar:

---

### Post by Mr_Freez3 on 2009-10-19
sopadeajo,

Go [**here**]("http://ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors") and follow the first post, it works on my Jaunty machine.  The script detects more information, which might solve your problem with the "0" temperature reading.

Don't see anything wrong with your .conkyrc, so I was thinking maybe lm-sensors isn't detecting all your sensors.

Hope this might help.

---

