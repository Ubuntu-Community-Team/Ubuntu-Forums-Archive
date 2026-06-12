---
title: "Help with conky - help required here and there"
date: 2011-03-19
forum: General Help
---

### Post by indus_credo on 2011-03-19
Hi people

I am a total newbie to Ubuntu. Ok! Not total, but to quite an extent. And it is the first time I am seeking help here on the Ubuntu forums (until now I was just going through the current forums and they have been more than helpful)
I am facing 2 issues with my conky setup (Hint: I managed to install it..yay!)

1. I conky file which I copied was from one of the forums here and it had sda1 in the HD monitor but I have my '/' in sda5 (sda2 is Zombian OS, sda3 is extended and under that its sda5 and sda6(swap)). So, what I did was replace all sda1 with sda5 but the terminal reads: statfs '/media/sda3' - no such file or directory. Same is the case if I try with sda3
Conky displays the hda1 as 100% at all times

So, I don't know what I am doing wrong here.
:(

2. I am not able to get the conkyweather thingy to work. I read the posts in:

[http://ubuntuforums.org/showthread.php?t=869328&highlight=conky](http://ubuntuforums.org/showthread.php?t=869328&highlight=conky)

But I couldn't find what to do. Or maybe I missed onto something. I have registered on weather.com on the link mentioned in that forum and received a couple of emails but don't know what to do next.

If any light can be shed on these two issues, it'd be great.
Next question after this would be what are .lua files and what are these used for?

If I am posting it at the wrong place, please feel free to move it.
:D

---

### Post by Quackers on 2011-03-19
Where are you using the sda1/sda5 entries?
Please post the relevant sections of your .conkyrc within code tags (for code tags click on new reply (not quick reply) then click on the # symbol in the toolbar and paste text in between)
The weather is a lot more complicated. For a starter, the emails you have received will include a XOAP_PARTNER_ID and a XOAP_LICENCE_KEY. These must be entered into their respective fields in your .conkyForecast.config file, which is a hidden file in your home folder - press ctrl+h to unhide them).

---

### Post by indus_credo on 2011-03-19
> **Quackers said:**
> Where are you using the sda1/sda5 entries?
Please post the relevant sections of your .conkyrc within code tags 

I didn't read where all sda1 was in the conky file. What I did was find sda1 and replace all by sda3 (and sda5). Here is the code:

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
# 
 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 3.0
 
# Minimum size of text area
# minimum_size 250 5
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
 
# Stippled borders?
stippled_borders 3
 
# border margins
border_margin 9
 
# border width
border_width 10
 
# Default colors and also border colors, grey90 == #e5e5e5
default_color grey
 
own_window_colour brown
own_window_transparent yes
 
# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
 
# Gap between borders of screen and text
gap_x 10
gap_y 10
 
# stuff after 'TEXT' will be formatted on screen
 
TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine
 
${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
 
${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color
 
Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
hda1:  ${fs_free_perc /media/sda3}%   ${fs_bar 6 /media/sda3}$color
 
${color orange}NETWORK (${addr wlan0}) ${hr 2}$color
Down: $color${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,140 000000 ff0000} ${alignr}${upspeedgraph wlan0 
25,140 000000 00ff00}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}
```
> The weather is a lot more complicated. For a starter, the emails you have received will include a XOAP_PARTNER_ID and a XOAP_LICENCE_KEY. These must be entered into their respective fields in your .conkyForecast.config file, which is a hidden file in your home folder - press ctrl+h to unhide them).That's the catch. I installed conkyforecast but there is no .conkyforecast file anywhere. I tried "whereis" but it didn't find anything.
:(
And I think I need to prepare myself with the complicated stuff now, not to mention with help from you guys.

---

### Post by stinkeye on 2011-03-20
In the terminal run
```
df
```

eg my df results
```
glen@MavMusic:~$ df
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sdc1             30961664   5356968  24031936  19% /
none                   1022552       328   1022224   1% /dev
none                   1030368       196   1030172   1% /dev/shm
none                   1030368       324   1030044   1% /var/run
none                   1030368         0   1030368   0% /var/lock
/dev/sdc3             44924308  16106708  26535568  38% /home
/dev/sda5            118997832  25347368  87506408  23% /media/UBUP
/dev/sda2            242284296  51608140 190676156  22% /media/Storage
/dev/sda1            123218516  72537068  50681448  59% [COLOR="Magenta"]**/media/XP**[/COLOR]
```
Use what ever is shown in the [COLOR="#ff00ff"]**mounted on**[/COLOR] column.


As for conkyforecast you need to copy the **conkyForecast.config** file
from /usr/share/conkyforecast to your home folder and make hidden.
```
cp /usr/share/conkyforecast/conkyForecast.config ~/.conkyForecast.config
```


Now you need to edit the **~/.conkyForecast.config**
```
gedit ~/.conkyForecast.config
```


...and add your 
```
DEFAULT_LOCATION = [COLOR="SandyBrown"]???????[/COLOR]
XOAP_PARTNER_ID = [COLOR="#f4a460"]???????????[/COLOR]
XOAP_LICENCE_KEY = [COLOR="#f4a460"]????????????[/COLOR]
```

Get your **DEFAULT_LOCATION** from the address bar when you go to
weather.com and choose your location. eg **ASXX0233**

PARTNER_ID and LICENCE_KEY are sent by email when you register
@ [**_[COLOR="DarkRed"]http://www.weather.com/services/xmloap.html[/COLOR]_**]("http://www.weather.com/services/xmloap.html")

P.S The conky you posted doesn't make use of conkyforecast.
To test, run the example config included with conkyforecast.
```
**conky -c /usr/share/conkyforecast/example/conkyrc &**
```
You should see output similar to attached pic.

---

### Post by Quackers on 2011-03-20
As stinkeye points out, .conkyForecast has a capital F :-)
I forgot about copying it first! It's been a while since I did it :-)

---

### Post by stinkeye on 2011-03-20
> **Quackers said:**
> As stinkeye points out, .conkyForecast has a capital F :-)
I forgot about copying it first! It's been a while since I did it :-)
Yeah, I had to have a reread of kaivalagi's page and do some copy and paste.
;)

---

### Post by indus_credo on 2011-03-20
First thing tomorrow is trying this..;)

---

### Post by indus_credo on 2011-03-23
Sorry for the delay in update guys. My system crashed on me. I use Zombian OS for MATLAB as I don't have a copy for Linux. And then when I tried to reinstall, it would tell me that there is no hard drive. Strange!
So, I had to install Ubuntu, install Windows over it and then again install Ubuntu.
:mad:

Well, coming to the topic. I am trying a conky file while writing this up. Will update when I am done.
;)

---

