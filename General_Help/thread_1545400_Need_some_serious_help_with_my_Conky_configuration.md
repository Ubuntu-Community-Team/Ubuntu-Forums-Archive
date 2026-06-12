---
title: "Need some serious help with my Conky configuration!"
date: 2010-08-03
forum: General Help
---

### Post by Mi11z on 2010-08-03
**_[CENTER]Need some serious help with my Conky configuration![/CENTER]_**


**_*[COLOR="Red"]PLEASE SCROLL DOWN TO KEEP UP TO DATE WITH MY SITUATION![/COLOR]*_**

Yes hey folks well heres the deal, i'm customizing my conky to look like this:

[http://sen7.deviantart.com/#/d2i5f45](http://sen7.deviantart.com/#/d2i5f45)

And have followed the instructions included to the letter but i had another conky config scipt running, this one which i just tried (you know something basic to get me started with conky)

[http://www.junauza.com/2009/03/installset-up-conky-on-ubuntu.html](http://www.junauza.com/2009/03/installset-up-conky-on-ubuntu.html)

and i forgot all about the old config when i moved on to the next so now i'm left with blank config file and the end result is this:

[IMG]http://i371.photobucket.com/albums/oo151/xl-mi11z/Other/Screenshot-2-1.png[/IMG]

see it hasn't gone to plan lol has not turned out as it should have , it's cut off below the screen line and because the config file issue i can't actually continue to configure and finish the last step,

i will also point out that i want the end result of conky to be in window form meaning i can drag and drop the conky where i want on the screen.

anyway hope you guys can help me and really a simple solution would be if someone could provide me with a default untouched ```
.conkyrc
``` file. please thanks again. :)

---

### Post by Mi11z on 2010-08-03
bbbbump.

---

### Post by Smart Viking on 2010-08-03
> **Mi11z said:**
> bbbbump.

Don't bump so early dude.

Anyways remove conky, delete the config file in the home folder and then install it, i imagine that would work... :)

---

### Post by Mi11z on 2010-08-03
> **Smart Viking said:**
> Don't bump so early dude.

Anyways remove conky, delete the config file in the home folder and then install it, i imagine that would work... :)

My apologies and thank you it's worth a try, was getting inpatient. :)

---

### Post by Maverick_Meerkat on 2010-08-03
Greetings,
 

To fix the problem try changing:

```
/mnt/music
```

to

```
/media/music
```

You can also extract the sample file the using the following command:

```
zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc
```

Here is an example .conkyrc that works properly

```
# UBUNTU-CONKY
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
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
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

# stuff after &#8216;TEXT&#8217; will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${freq}MHz Load: ${loadavg} Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME PID CPU% MEM%
${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM: $memperc% ${membar 6}$color
Swap: $swapperc% ${swapbar 6}$color

Root: ${fs_free_perc /}% ${fs_bar 6 /}$color
hda1: ${fs_free_perc /media/hda1}% ${fs_bar 6 /media/hda1}$color
hdb3: ${fs_free_perc /media/hdb3}% ${fs_bar 6 /media/hdb3}

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}
```

If the network connections graph does not work, you will have to change all &#8220;eth0&#8243; references to &#8220;ppp0&#8243; (for modem) or &#8220;ath0&#8243; (for other devices).

BTW that is a slick looking conky @ deviant art!

---

### Post by Mi11z on 2010-08-03
> BTW that is a slick looking conky @ deviant art!

I know i was happy with my find too, and thank you also. :)

---

### Post by Mi11z on 2010-08-03
Heres where i'm at , managed to fix the screen orientation problem (found the script option), all or most other problems corrected still senor issues their not as responsive as they should be even the clock on conky appears to be frozen, little more help then please guys.........? =/

[IMG]http://i371.photobucket.com/albums/oo151/xl-mi11z/Other/458uf48.png[/IMG]

---

### Post by Mi11z on 2010-08-03
bump, please help... :-? :(

---

### Post by jasonpickles on 2010-08-03
It looks like you haven't registered with weather.com to get the XOAP_PARTNER_ID & XOAP_LICENCE_KEY.Once you register, you'll get an email with this info. Put the info in the conkyForecast.config file, and that should help out with the errors showing in Terminal.

---

### Post by Mi11z on 2010-08-04
> **jasonpickles said:**
> It looks like you haven't registered with weather.com to get the XOAP_PARTNER_ID & XOAP_LICENCE_KEY.Once you register, you'll get an email with this info. Put the info in the conkyForecast.config file, and that should help out with the errors showing in Terminal.

Thank you and it's free to register right, i'll find out anyway cheers.

---

### Post by Mi11z on 2010-08-04
> **jasonpickles said:**
> you haven't registered with weather.com to get the XOAP_PARTNER_ID & XOAP_LICENCE_KEY.Once you register, you'll get an email with this info.
 

Once registered where do you go from there to get this information and to get the e-mail sent?

---

### Post by stlsaint on 2010-08-04
It seems that the email which is sent to you should contain all this information.

---

### Post by Mi11z on 2010-08-04
> **stlsaint said:**
> It seems that the email which is sent to you should contain all this information.

No i mean what option do you to select from here to "get" the email sent ?

[IMG]http://i371.photobucket.com/albums/oo151/xl-mi11z/Other/Screenshot-3.png[/IMG]

---

### Post by stinkeye on 2010-08-04
[**_[COLOR="DarkRed"]Conky Weather Forecast Python Script[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=869328&highlight=conkyforecast")
Scroll down to the **[COLOR="Blue"]Weather.com XOAP Service Registration[/COLOR]** section.

---

### Post by Mi11z on 2010-08-04
> **stinkeye said:**
> [**_[COLOR="DarkRed"]Conky Weather Forecast Python Script[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=869328&highlight=conkyforecast")

Cheers again stinkeye! forgot about that thread.

ahh the "Weather.com XOAP Service Registration" section happiness :D

---

