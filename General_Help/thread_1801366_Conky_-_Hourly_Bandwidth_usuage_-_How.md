---
title: "Conky - Hourly Bandwidth usuage - How?"
date: 2011-07-10
forum: General Help
---

### Post by drewsus on 2011-07-10
Hello,
So, my mother is out in the deep country and all we can get is Xplornet Satellite internet. They have a fair access policy (FAP) that says they will (and definitely do) throttle your speeds if you download more than 50MB or upload more than 5.5MB in one hour. This restriction resets hourly. As you can imagine, this is fairly limiting, but we have to live with what we have as there are no other options specifically where we live.   
Right now, I have Conky configured to show the **${totalup wlan0}** and **${totaldown wlan0}**, but that is ***per session***.
[IMG]http://i.imgur.com/r855k.png[/IMG]
In this example, since the computer started, 8.74MB have been downloaded and 1.95MB uploaded. 

*However*, this information is somewhat irrelevant as we really only need to know the current usage starting at the top of the hour. Maybe even show the previous hour too. 

Can anyone help me out here? 
Thank you, 
Drew

---

### Post by Habitual on 2011-07-10
Drew:

I'm intrigued by this request... I am checking into it.

---

### Post by drewsus on 2011-07-10
Thank you, sir!   
I await your[s and potentially other people's] findings!

---

### Post by Habitual on 2011-07-10
No problemo!

I am an idiot that doesn't read enough of a post. :(

still checking...

---

### Post by Habitual on 2011-07-10
Drew:

You have vnstat installed? ;)
if not, please do so with
```
sudo apt-get install -y vnstat && vnstat-create-db wlan0
```

to start collecting traffic stats for wlan0.

Script and/or configuration to follow.
I just installed it myself, so I am also starting the collection process.

---

### Post by Habitual on 2011-07-10
Drew:

making pretty good progress. :)

Should have the solution here real quick.

edit: almost "there"
I LOVE this stuff.

---

### Post by Habitual on 2011-07-10
Drew:

Using your favorite editor, make a shell script with these contents:
```

#!/bin/bash
echo "Tx (MiB) for this hour is" $(for i in `date +%H` ; do vnstat --dumpdb | grep "h;$i" ; done | cut -c 17- | cut -d\; -f1)
echo "Rx (MiB) for this hour is" $(for i in `date +%H` ; do vnstat --dumpdb | grep "h;$i" ; done | cut -c 17- | cut -d\; -f2)

```

say you save it as /home/drew/Documents/hourly_stats.sh
Open your terminal and type:
```
chmod 700 /home/drew/Documents/hourly_stats.sh
```

in your conky rc file stick this in there:
${execi 60 /home/drew/Documents/hourly_stats.sh}

References used:
[http://man.cx/vnstat](http://man.cx/vnstat)
[http://man.cx/conky](http://man.cx/conky)

My conky version is:
Conky 1.8.0

It's been a fun 2 hours, I hope you got as much out of this as I did.

If you need further help, I'll check this thread every couple of hours or shoot me a PM with your email address and we can tune it up.

Enjoy!

---

### Post by kanishkdudeja on 2011-07-10
@habitual..

could you please help me out too?

im using conky today for the first time..

copied a script from somewhere..

but in the network usage its showing 0..

i use Reliance Net Connnect data card..

here is the script..

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
hda1:  ${fs_free_perc /media/sda1}%   ${fs_bar 6 /media/sda1}$color
 
${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown ppp} ${alignr}Total: ${totalup ppp}
${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}
 
${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}
```

---

### Post by Habitual on 2011-07-10
kanishkdudeja:

sure!

open a terminal and type:
```
ifconfig
```

paste the output.

---

### Post by kanishkdudeja on 2011-07-10
```
kanishk@kanishk-Inspiron-1525:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:9b:d1:4a:ab  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1f:e1:ce:37:65  
          inet6 addr: fe80::21f:e1ff:fece:3765/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1736 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1736 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:137255 (137.2 KB)  TX bytes:137255 (137.2 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:115.242.101.194  P-t-P:220.224.141.129  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:25508 errors:25 dropped:0 overruns:0 frame:0
          TX packets:25213 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:18645853 (18.6 MB)  TX bytes:3697940 (3.6 MB)

```

---

### Post by Habitual on 2011-07-10
kanishkdudeja:

try changing ppp or eth0 to ppp0 in/for "Network Usage".
Not sure which one (or multiples) in your code here:
```

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown ppp} ${alignr}Total: ${totalup ppp}
```

HTH.

---

### Post by kanishkdudeja on 2011-07-10
oh wow..its worked..thanks a lot..:)

---

### Post by Habitual on 2011-07-10
You're Very Welcome.
glad it worked out.

Have a Great Day!

---

### Post by kanishkdudeja on 2011-07-10
same to you..:)

thanks again..:)

---

### Post by kanishkdudeja on 2011-07-10
Another problem.


How can i set conky to be only visible on the desktop?

not on the browser windows and the file windows?

---

### Post by Habitual on 2011-07-11
I'd need a screenshot of the "effect" you are referring to please...

Here's what I see when I use your code, perhaps you can use that as a reference to the issue at hand?
[http://susepaste.org/52967795](http://susepaste.org/52967795)

rapidly peeking at your code, you could try 
```
own_window_type desktop
```

How do you start your conky?

---

### Post by Habitual on 2011-07-11
This suggestion did not work?
[http://ubuntuforums.org/showpost.php?p=11034809&postcount=3](http://ubuntuforums.org/showpost.php?p=11034809&postcount=3)

---

### Post by kanishkdudeja on 2011-07-11
Yes that thread solved my problem :)

---

