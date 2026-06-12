---
title: "Conky won't start"
date: 2010-05-29
forum: General Help
---

### Post by Foxblood on 2010-05-29
Hi, 

I started this tutorial [http://ubuntuforums.org/showthread.php?t=867076&highlight=conky+tutorial](http://ubuntuforums.org/showthread.php?t=867076&highlight=conky+tutorial). When I try to start Conky I get this:


Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
	This program is calling the Imlib call:

	imlib_context_free();

	With the parameter:

	context

	being NULL. Please fix your program.

What'

---

### Post by VCoolio on 2010-05-29
Please post your conky config file, so the gurus can take a look.

---

### Post by Foxblood on 2010-05-30
Here's my Conky. I haven't changed anything in it.



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

alignment top_left
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
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_type desktop
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no

TEXT
${scroll 16 $nodename - $sysname $kernel on $machine | }
$hr
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
${color grey}Frequency (in GHz):$color $freq_g
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$hr
${color grey}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking:
Up:$color ${upspeed eth0} ${color grey} - Down:$color ${downspeed eth0}
$hr
${color grey}Name              PID   CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

---

### Post by soderstrom on 2010-05-31
I got the same problem, also running 64-bit version of Ubuntu 10.04. I read about some other people out there who having same problems and most said that you have to configure conky to delay autostart on boot-up because of some problems with compiz I think it was? Should not say to much tho because I don't have the information available where I read this and the solution I found doesn't work for me.

I made a script that looks like this

```
#!/bin/bash
sleep 25 && conky -c ~/.conkytheme/conkyrc ;
```

used gedit and saved the file as startupconky.sh

Then add startupconky.sh to system - preferences - startup applications

This should have done the trick, but nothing happens, but when I run the script in terminal, my conky shows up after 25 seconds. The strange part is tho after closing the terminal conky also dissapair, but then comes back after some seconds?

Donno if this was much of help but maybe there are someone else out there with similar problem and maybe the above works for you. It doesn't for me. If I find a answer to this and yours problem, I will post it here.

---

### Post by SoFl W on 2010-05-31
> **Foxblood said:**
> When I try to start Conky I get this: <snip> 

try using "conky -c /PATH/TO/.conkyrc" from the command line to make sure it is picking up the correct script.


> **soderstrom said:**
> 
I made a script that looks like this

```
#!/bin/bash
sleep 25 && conky -c ~/.conkytheme/conkyrc ;
```
10 seconds is more than enough.  The only difference I have is the "-d" parameter. (daemonize, fork to background)
```
#!/bin/bash
sleep 10 && conky -d -c /PATH/TO/.conkyrc;
exit
```Did you check permissions on the conky start script? It all needs to be executable.
> **soderstrom said:**
> 
 The strange part is tho after closing the terminal conky also dissapair, but then comes back after some seconds?

Not strange at all, you closed the terminal that was running the program, perhaps then the start-up script conky is finally starting.  Sometimes it takes a while for mine to start, usually waiting for the public ip section to retrieve data.  It will have a small square in the upper left area where my conky is suppose to be.  Once it gets the info the script completes and displays.

---

### Post by soderstrom on 2010-05-31
> **SoFl W said:**
> try using "conky -c /PATH/TO/.conkyrc" from the command line to make sure it is picking up the correct script.



10 seconds is more than enough.  The only difference I have is the "-d" parameter. (daemonize, fork to background)
```
#!/bin/bash
sleep 10 && conky -d -c /PATH/TO/.conkyrc;
exit
```Did you check permissions on the conky start script? It all needs to be executable.


Not strange at all, you closed the terminal that was running the program, perhaps then the start-up script conky is finally starting.  Sometimes it takes a while for mine to start, usually waiting for the public ip section to retrieve data.  It will have a small square in the upper left area where my conky is suppose to be.  Once it gets the info the script completes and displays.

Thanks for the reply, even tho I noticed I posted my question in the wrong thread. Had two forums open with similar questions...

I did what you suggested and also checked permission and everything was like it should. But the original conky configuration shows up instead for some reason,a black and ugly one. This one disappears tho when I right-click on the desktop? The conky configuration I am using is [this one]("http://www.omgubuntu.co.uk/2010/05/easy-to-use-lucid-themed-conky-bar.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28Omg%21+Ubuntu%21%29") 

I have installed conky-full from ubuntu software center, so will try and install the one mentioned at the guide instead.

---

