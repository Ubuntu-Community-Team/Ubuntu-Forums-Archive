---
title: "Problem with Conky"
date: 2010-08-01
forum: General Help
---

### Post by uRock on 2010-08-01
Conky seems to be doing the always on top thing. Is there any way to make it stay behind the open windows? As you can see in the screenshot, the FF window stops just above the Conky.

Any help is appreciated,
uRock

---

### Post by uRock on 2010-08-01
Here is the conf file for conky.
```
# Locale, fonts and font sizes.
use_xft yes
xftfont Droid Sans:size=9
override_utf8_locale yes

# Conky performance
update_interval 1
total_run_times 0
double_buffer yes
no_buffers yes
net_avg_samples 2
text_buffer_size 1024

# Execute it in its own window
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Borders, margins.
draw_borders no
border_margin 1

# Own window color
own_window_colour 393834

# Font colors
default_color B7B2AD
#default_color EFEEED

# Text shadows
draw_shades no

# Header colors
color0 DD3A21

# Minimum dimensions
minimum_size 1440 0

# Conky positioning.
alignment bottom_left
gap_x 0
gap_y 30

# Output
TEXT
${image ~/.conkytheme/pix/frame.png -p 0,0 -s 1280x180}
${voffset 20}${font Droid Sans:style=Bold:size=12}${color0}${goto 256}Disks:${goto 512}Network:${goto 768}Temperatures:${goto 102$
${voffset 6}${goto 256}System (/):${goto 380}${fs_used /} / ${fs_size /}${goto 512}Upspeed: ${goto 612}${upspeedgraph eth0 10,100$


```

---

### Post by aklein84 on 2010-08-01
post your config file. 

Might have to change the "own_window" to yes and "own_window_type" to override. hope this helps

Scratch what I posted that comment right as you posted your config file

---

### Post by Raymond2201 on 2010-08-01
I think it's something to do with compiz or other decorators. if i remember rightly you have to put a delay on its startup (5 seconds or so) to allow compiz or whatever to start up.

```

(sleep 5s && conky) &

```

something to try at least

---

### Post by uRock on 2010-08-01
> **Raymond2201 said:**
> I think it's something to do with compiz or other decorators. if i remember rightly you have to put a delay on its startup (5 seconds or so) to allow compiz or whatever to start up.

```

(sleep 5s && conky) &

```something to try at least
Thanks Raymond. I'll give it a try.

---

### Post by uRock on 2010-08-01
> **uRock said:**
> Thanks Raymond. I'll give it a try.
That didn't work. Now conky isn't starting.

---

### Post by Raymond2201 on 2010-08-01
where did you add that?

---

### Post by 5BallJuggler on 2010-08-01
> **uRock said:**
> Here is the conf file for conky.
```
# Locale, fonts and font sizes.
use_xft yes
xftfont Droid Sans:size=9
override_utf8_locale yes

# Conky performance
update_interval 1
total_run_times 0
double_buffer yes
no_buffers yes
net_avg_samples 2
text_buffer_size 1024

# Execute it in its own window
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Borders, margins.
draw_borders no
border_margin 1

# Own window color
own_window_colour 393834

# Font colors
default_color B7B2AD
#default_color EFEEED

# Text shadows
draw_shades no

# Header colors
color0 DD3A21

# Minimum dimensions
minimum_size 1440 0

# Conky positioning.
alignment bottom_left
gap_x 0
gap_y 30

# Output
TEXT
${image ~/.conkytheme/pix/frame.png -p 0,0 -s 1280x180}
${voffset 20}${font Droid Sans:style=Bold:size=12}${color0}${goto 256}Disks:${goto 512}Network:${goto 768}Temperatures:${goto 102$
${voffset 6}${goto 256}System (/):${goto 380}${fs_used /} / ${fs_size /}${goto 512}Upspeed: ${goto 612}${upspeedgraph eth0 10,100$


```

These are the relevant lines in all of my conky's

```
own_window_colour black
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
own_window_type root
own_window yes
```

hope it helps

---

### Post by uRock on 2010-08-01
I added it to the command line in Startup Applications. Is it supposed to be in a different file?  I have unchecked it in the Startup Preferences and created a launcher for the panel for the time being. WIth the launcher it starts up properly, so making it sleep on startup will definitely fix the problem.

Thanx,
uRock

---

### Post by Raymond2201 on 2010-08-01
right, if this does not work then it's something else other than the order of starting.

create file in your home folder called conky_start.sh, open it with your text editor and paste this in:

```

#!/bin/bash
sleep 5 && conky;

```Change the file properties so its executable, then add this file location into your startup.

EDIT: remember to remove the other piece of code i gave you from your startup ;)

---

### Post by 2hot6ft2 on 2010-08-01
What I did for the delay was created a new document in my home folder called Start-Conky and put this in it
```
    #!/bin/bash
    sleep 30
    conky &
    exit 0
```
Made it executable, right click on it and set the permissions in the permissions tab to set it.
Then went to
System > Preferences > Startup Applications
Click Add, then give it a name and browse to the file that you created and select it, click Save then Close.
Each time the computer starts conky will start 30 seconds later.
:popcorn:

---

### Post by uRock on 2010-08-01
> **Raymond2201 said:**
> right, if this does not work then it's something else other than the order of starting.

create file in your home folder called conky_start.sh, open it with your text editor and paste this in:

```

#!/bin/bash
sleep 5 && conky;

```Change the file properties so its executable, then add this file location into your startup.

EDIT: remember to remove the other piece of code i gave you from your startup ;)
Got it working right. I had to alter it a bit so that it didn't open the default black and blinky conky. Here is what I have;
```
uRock more conky_start.sh
#!/bin/bash
sleep 5 && conky -c /home/rabbit/.conkytheme/conkyrc;
uRock ls -l conky_*.*
-rwx--x--x 1 rabbit rabbit 66 2010-08-01 11:52 conky_start.sh
uRock 

```

Thank you all for helping out,
uRock

---

### Post by uRock on 2010-08-01
I did a restart and it appears that everything else waited for conky to finish sleeping before loading, therefore it is still giving me the same grief. [s]What do I add to the sleep line that will allow other processes to run, but not the conky command?[/s] Nevermind, I am just going to use a home made launcher to start it.

Thanx, 
uRock

---

### Post by 5BallJuggler on 2010-08-01
> **uRock said:**
> I did a restart and it appears that everything else waited for conky to finish sleeping before loading, therefore it is still giving me the same grief. [s]What do I add to the sleep line that will allow other processes to run, but not the conky command?[/s] Nevermind, I am just going to use a home made launcher to start it.

Thanx, 
uRock

I doubt that it is anything to do with the timing you start conky, it is to do with the window type, check out my post on the first screen and see what that does.

---

### Post by stinkeye on 2010-08-01
> **uRock said:**
> I did a restart and it appears that everything else waited for conky to finish sleeping before loading, therefore it is still giving me the same grief. [s]What do I add to the sleep line that will allow other processes to run, but not the conky command?[/s] Nevermind, I am just going to use a home made launcher to start it.

Thanx, 
uRock
If your using compiz use this script to start.It will delay the starting of conky until compiz has loaded.
**[SIZE="3"]The compiz Dbus plugin must be enabled.[/SIZE]** CCSM > utility > Dbus
```
#! /bin/bash
until [ "$done" = "true" ]
do
	if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
	then
                DISPLAY=:0.0 [COLOR="Magenta"]conky[/COLOR] >/dev/null 2>&1 &
                
		done="true";
	else
		echo "Compiz Loading"
		done="false"
		sleep 5;
	fi
done
exit 0
```
Make executable and link to it in startup applications.
[COLOR="#ff00ff"]You can change **conky** to **conky -c /home/rabbit/.conkytheme/conkyrc**[/COLOR]
if that's the way you start it.

If you save your conky config as .conkyrc in your home folder you can load that config by just running **conky**

---

### Post by uRock on 2010-08-01
> **stinkeye said:**
> **<snip>**

Where do I add the script or do I need to make a file with the text in it and add it to startup apps?

> **5BallJuggler said:**
> I doubt that it is anything to do with the  timing you start conky, it is to do with the window type, check out my  post on the first screen and see what that does.I have all of those lines except for the root and color line in the file already.

---

### Post by stinkeye on 2010-08-01
> **uRock said:**
> Where do I add the script or do I need to make a file with the text in it and add it to startup apps?
Just create an empty file and paste script in and save wherever you keep your conky stuff.

Right click on file properties > permissions
and tick execute.

Link to it via the command box (click browse)
when you add to startup applications.

---

### Post by uRock on 2010-08-01
> **stinkeye said:**
> Just create an empty file and paste script in and save wherever you keep your conky stuff.

Right click on file properties > permissions
and tick execute.

Link to it via the command box (click browse)
when you add to startup applications.
Cool, thanx.

---

