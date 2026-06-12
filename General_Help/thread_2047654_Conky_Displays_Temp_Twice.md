---
title: "Conky Displays Temp Twice"
date: 2012-08-25
forum: General Help
---

### Post by Petro Dawg on 2012-08-25
I'm very new to Conky and I succesfully got my CPU temp to display, however, it appears twice and in a very bad format.  

To get started, here  is my pertinent conkyrc code:
```
CPUtemp: ${execi 8 sensors | grep -A 1 'temp1' | cut -c13-19}C
```

This is my sensors output in terminal:
```
:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +55.0°C  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +55.1°C  (high = +70.0°C)
                       (crit = +115.5°C, hyst = +110.5°C)
```

This is my conky output:
```
CPUtemp:  +55.0


  +55.1
       C
```

I kinda see why it is displaying both temp1's, but I don't know how to keep it from doing so, or how to format the out put in a good way.  I would prefer it just to display the PCI adapter temp1.  Any ideas how I can do this?  

Thanks in advance for any help.

---

### Post by Rexilion on 2012-08-25
Maybe

```
CPUtemp: ${execi 8 sensors k10temp-pci-00c3 | grep -A 1 'temp1' | cut -c13-19}C
```

??

---

### Post by Petro Dawg on 2012-08-25
Well played around with my cockyrc code piece by piece figuring out what each part of the code was doing.

Fixed the issue with the following code:
> CPU Temp: $alignr${execi 1 sensors | grep 'high' | cut -c14-19}CI just needed to find a word unique to the sensor output line I was wanting to copy from, 'high' for example.  (Most of you are probably saying 'DUH', but remember I never heard of conky till yesterday ;)  ) 

I couldn't figure out what the number following 'execi' did, all I could figure out is that the code would not work if set to 0.  Anyone knows what that number does?

Code also works fine without the 'A -1' following the 'grep' , so not sure what the 'A -1' does either.

---

### Post by Gillingham on 2012-08-25
There are several slightly different conky variables to run an external command.

These are

exec 
which executes a shell command each time conky updates according to the update_interval command.

execi x
executes the shell command every x seconds, which can be different from the update_interval.

These 2 will just out put the result of a script. 

2 other variables I use are execp and execpi where conky will parse the output as well, so you can change the way conky looks based upon the output of the script.   

David

---

### Post by Petro Dawg on 2012-08-25
> **Gillingham said:**
> There are several slightly different conky variables to run an external command.

These are

exec 
which executes a shell command each time conky updates according to the update_interval command.

execi x
executes the shell command every x seconds, which can be different from the update_interval.

These 2 will just out put the result of a script. 

2 other variables I use are execp and execpi where conky will parse the output as well, so you can change the way conky looks based upon the output of the script.   

David

Thanks, makes sense.  I will just use 'exec' and update with the set update_interval then.

Any idea on what the "A -1" is used for?  It was in the source code I started from, but it didn't seem to have any apparent effect when I removed it.

---

### Post by Petro Dawg on 2012-08-25
I'll tinker around with it some more.  However, I'm rather pleased with the following output:
[[IMG]http://farm8.staticflickr.com/7263/7857847928_938e32bac8_n.jpg[/IMG]]("http://farm8.staticflickr.com/7263/7857847928_938e32bac8_b.jpg")

conkyrc code:
```
background no
font Ubuntu:bold:size=11
use_xft yes
xftalpha 0.9
update_interval 3.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 180 5
maximum_width 180
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color cccccc
default_shade_color black
default_outline_color green
alignment top_right
gap_x 12
gap_y 35
no_buffers yes
uppercase no
cpu_avg_samples 4
override_utf8_locale no
uppercase no

TEXT

CPU Temp: $alignr${exec sensors | grep 'high' | cut -c16-19}C

High: ${exec sensors | grep 'high' | cut -c34-37}C  $alignr Crit: ${exec sensors | grep 'crit' | cut -c33-37}C

CPU: ${alignr}${freq} MHz
Core 1 ${alignr}${cpu cpu1}%
${cpubar 4 cpu1}
Core 2 ${alignr}${cpu cpu2}%
${cpubar 4 cpu2}
${top name 1}$alignr${top cpu 1}
${top name 2}$alignr${top cpu 2}
${top name 3}$alignr${top cpu 3}
${top name 4}$alignr${top cpu 4}
${top name 5}$alignr${top cpu 5}

RAM: ${alignr}$memmax
Active: ${alignr}$mem ($memperc%)
${membar 4}
${top_mem name 1}$alignr${top_mem mem 1}
${top_mem name 2}$alignr${top_mem mem 2}
${top_mem name 3}$alignr${top_mem mem 3}
${top_mem name 4}$alignr${top_mem mem 4}
${top_mem name 5}$alignr${top_mem mem 5}

Filesystem
Root: ${alignr}${fs_used /} / ${fs_size /}
${fs_bar 4 /}
Home: ${alignr}${fs_used /home} / ${fs_size /home}
${fs_bar 4 /home}

Network: ${alignr}(${addr wlan0})
Down: ${downspeed wlan0}/s ${alignr}(${totaldown wlan0})
${downspeedgraph wlan0 000000 775555}
Up: ${upspeed wlan0}/s ${alignr}(${totalup wlan0})
${upspeedgraph wlan0 000000 557755}$color
```

---

### Post by Gillingham on 2012-08-25
The grep -A x means that grep will output the 1st x lines after the match.  Rather than just the line the match is on, so in your case with x=1 it isn't necessary.


David

---

### Post by Petro Dawg on 2012-08-25
> **Gillingham said:**
> The grep -A x means that grep will output the 1st x lines after the match.  Rather than just the line the match is on, so in your case with x=1 it isn't necessary.


David

Thanks again, you have been most helpful.

---

