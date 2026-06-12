---
title: "Conky config problem &quot;missing text block in configuration&quot;"
date: 2010-05-06
forum: General Help
---

### Post by MorrisseyJ on 2010-05-06
Hi i am having a problem with Conky:

When i try and run it from the terminal i get:

> Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_context_free();

    With the parameter:

    context

    being NULL. Please fix your program.I have tried reinstalling but i still get this msg when i try and run from the terminal. I see that this has been dealt with in this [thread]("http://ubuntuforums.org/showthread.php?t=1295621"). The problem is that i am still new to Linux and don't know what to do with this:

> You need a conky config file. The first line of the message suggests you  don't have one, at least not one with config first, then a line that  says "TEXT" and then the contents you want to display. Google for conky  and you'll find plenty of configs. The default path for it is ~/.conkyrc  and if you run "conky -C > ~/.conkyrc" you´ll get a default config  file that you can tweak. 
Read the last pages of [this thread]("http://ubuntuforums.org/showthread.php?p=8006534#post8006534") for more inspiration and also you can  ask questions there (it's the sticky "howto of the week"). [Here]("http://conky.linux-hardcore.com/") you can  also find nice setups and howtos.

If you still have difficulties, post your conky config with your  question.Could someone tell me what i need to do to my config file - step by step would be great. 

Because the above suggested i post my conky config file i'll do that here in case its necessary. So here is what i think is my conky config.

> # Conky, a system monitor, based on torsmo
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
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}Any advice would be greatly appreciated.

---

### Post by MorrisseyJ on 2010-05-07
So i just ran the update manager. Had a whole bunch of stuff to install.

Thought that my conky troubles might have been related to an update issue. So i tried running conky again from the terminal. Conky then came up on my desktop. 

I then couldn't close it from the terminal, nor did it seem from the GUI. So i opened another terminal and did 'killall conky'. Conky shut down as did my first terminal.

Now however when i try and run conky from the terminal i get:

> Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_context_free();

    With the parameter:

    context

    being NULL. Please fix your program.So i must be doing something when i close conky. Can someone tell me what i am doing wrong in closing conky (how should i close the programme?) and possibly how to get conky back again.

---

### Post by bra|10n on 2010-05-07
> **MorrisseyJ said:**
> Hi i am having a problem with Conky:

When i try and run it from the terminal i get:

I have tried reinstalling but i still get this msg when i try and run from the terminal. I see that this has been dealt with in this [thread]("http://ubuntuforums.org/showthread.php?t=1295621"). The problem is that i am still new to Linux and don't know what to do with this:

Could someone tell me what i need to do to my config file - step by step would be great. 

Because the above suggested i post my conky config file i'll do that here in case its necessary. So here is what i think is my conky config.

Any advice would be greatly appreciated.

You might want to try losing the scroll section```
${scroll 16 $nodename - $sysname $kernel on $machine | }
```Change to ```
$nodename - $sysname $kernel on $machine
```

---

### Post by MorrisseyJ on 2010-05-07
Thanks for the idea but file is Read-Only so i can't change it. 

Any ideas?

---

### Post by MorrisseyJ on 2010-05-07
Ok, I am not understanding something here which is making the online forums very confusing.

I have two files the one is conky.conf which i pasted above. Its location is /etc/conky and it is a read only file

I also created a conkyrc, i will paste it below. I copied it off one of the many websites containing these things. Its location is now ~/.conkyrc

In all that i read about this people seem to use conkyrc and conky config file interchangeably. Can anyone tell me what each file does and and in which one my problem lies. 

I can't find anything in the conky documentation which clears this up.

Here is the conkyrc that i pasted:

> # UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades yes

---

### Post by MorrisseyJ on 2010-05-07
Ok, seems like solution (well at least something of a solution) was fairly simple and it also seems like i am an idiot.

I ended up pasting the conky.conf file (from /etc/conky) below the conkyrc file that i had created. 

It also appears that i had not copied all of the conkyrc file which means that config was never going to work and which makes me an idiot.

So it seems like if you get the msg:

> Conky: missing text block in configuration; exiting
 ***** Imlib2 Developer Warning ***** :
     This program is calling the Imlib call:
 
     imlib_context_free();
 
     With the parameter:
 
     context
 
     being NULL. Please fix your program.                      Then you can fix this by opening the terminal and typing 

> gedit ~/.conkyrcIn the open file paste all that was in the conky.config file from /etc/conky location. Save and close and run conky from the terminal. It now seems to work over and over again in the basic form that conky is downloaded. 

Now i guess i just need to find a conkyrc file which i like (which was the initial aim of all this).

I am still not sure what happened after i updated conky and then killed it.

---

### Post by MorrisseyJ on 2010-05-07
Just in case anyone has the problems that i had i'll keep this going:

it seems that the problem was that i tried the following which is mentioned on many posts.

I put this
> 
zcat /usr/share/doc/conky/examples/conky.conf.gz > ~/.conkyrcinto the terminal believing that it would take the config file (in ubuntu) and put it in my conkyrc file - which is what i now understand i have been doing. 

The output in the terminal was 
> gzip: /usr/share/doc/conky/examples/conky.conf.gz: No such file or directoryand what this did was clear my conkyrc file so that it was blank. Hence the message:
> Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_context_free();

    With the parameter:

    context

    being NULL. Please fix your program.So i am guessing that Lucid has changed the directory into which the conky.config file is placed which makes the zcat .... command useless.

---

