---
title: "No sound"
date: 2009-09-14
forum: General Help
---

### Post by Mitchcm on 2009-09-14
[SIZE=1]I have tried a lot and so has my friend we tried stuff in terminal.

[/SIZE]                                  [SIZE=1][COLOR=#cc0000](09:36:36 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#cc0000]**Manos: **[/COLOR][/SIZE][SIZE=1][COLOR=#000000][FONT=Comic Sans MS]**fire up terminal **[/FONT][/COLOR][/SIZE][SIZE=1]
[/SIZE][SIZE=1][COLOR=#cc0000](09:36:41 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#cc0000]**Manos: **[/COLOR][/SIZE][SIZE=1][COLOR=#000000][FONT=Comic Sans MS]**and give to it:**[/FONT][/COLOR][/SIZE][SIZE=1]
[/SIZE][SIZE=1][COLOR=#cc0000](09:36:44 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#cc0000]**Manos: **[/COLOR][/SIZE][SIZE=1][COLOR=#000000][FONT=Comic Sans MS]**sudo su**[/FONT][/COLOR][/SIZE][SIZE=1]
[/SIZE][SIZE=1][COLOR=#cc0000](09:36:47 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#cc0000]**Manos: **[/COLOR][/SIZE][SIZE=1][COLOR=#000000][FONT=Comic Sans MS]**then your password**[/FONT][/COLOR][/SIZE][SIZE=1]
[/SIZE][SIZE=1][COLOR=#cc0000](09:36:55 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#cc0000]**Manos: **[/COLOR][/SIZE][SIZE=1][COLOR=#000000][FONT=Comic Sans MS]**then**[/FONT][/COLOR][/SIZE][SIZE=1]
[/SIZE][SIZE=1][COLOR=#cc0000](09:36:56 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#cc0000]**Manos: **[/COLOR][/SIZE][SIZE=1][COLOR=#000000][FONT=Comic Sans MS]**killall pulseaudio**[/FONT][/COLOR][/SIZE][SIZE=1]
[/SIZE][SIZE=1][COLOR=#cc0000](09:37:02 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#cc0000]**Manos: **[/COLOR][/SIZE][SIZE=1][COLOR=#000000][FONT=Comic Sans MS]**then**[/FONT][/COLOR][/SIZE][SIZE=1]
[/SIZE][SIZE=1][COLOR=#cc0000](09:37:02 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#cc0000]**Manos: **[/COLOR][/SIZE][SIZE=1][COLOR=#000000][FONT=Comic Sans MS]**alsa force-reload**[/FONT][/COLOR][/SIZE][SIZE=1]
[/SIZE][SIZE=1][COLOR=#cc0000](09:37:06 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#cc0000]**Manos: **[/COLOR][/SIZE][SIZE=1][COLOR=#000000][FONT=Comic Sans MS]**then**[/FONT][/COLOR][/SIZE][SIZE=1]
[/SIZE][SIZE=1][COLOR=#cc0000](09:37:07 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#cc0000]**Manos: **[/COLOR][/SIZE][SIZE=1][COLOR=#000000][FONT=Comic Sans MS]**pulseaudio -D**[/FONT][/COLOR][/SIZE][SIZE=1]
[/SIZE][SIZE=1][COLOR=#cc0000](09:37:17 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#cc0000]**Manos: **[/COLOR][/SIZE][SIZE=1][COLOR=#000000][FONT=Comic Sans MS]**and try testing again**[/FONT][/COLOR][/SIZE][SIZE=1]
[/SIZE][SIZE=1][COLOR=#204a87](09:38:26 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#204a87]**Mitch:  **[/COLOR][/SIZE][SIZE=1]wow when i roece reloaded alsa it came up with lots
[/SIZE][SIZE=1][COLOR=#204a87](09:38:31 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#204a87]**Mitch:  **[/COLOR][/SIZE][SIZE=1]I HEAR SOUND
[/SIZE][SIZE=1][COLOR=#cc0000](09:38:47 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#cc0000]**Manos: **[/COLOR][/SIZE][SIZE=1][COLOR=#000000][FONT=Comic Sans MS]**problem fixed ?**[/FONT][/COLOR][/SIZE][SIZE=1]
[/SIZE][SIZE=1][COLOR=#204a87](09:39:05 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#204a87]**Mitch:  **[/COLOR][/SIZE][SIZE=1]maybe
[/SIZE][SIZE=1][COLOR=#204a87](09:39:09 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#204a87]**Mitch:  **[/COLOR][/SIZE][SIZE=1]no its gone
[/SIZE][SIZE=1][COLOR=#cc0000](09:39:17 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#cc0000]**Manos: **[/COLOR][/SIZE][SIZE=1][COLOR=#000000][FONT=Comic Sans MS]**what's gone ?**[/FONT][/COLOR][/SIZE][SIZE=1]
[/SIZE][SIZE=1][COLOR=#204a87](09:39:23 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#204a87]**Mitch:  **[/COLOR][/SIZE][SIZE=1]it was here the sound
[/SIZE][SIZE=1][COLOR=#204a87](09:39:26 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#204a87]**Mitch:  **[/COLOR][/SIZE][SIZE=1]then now its gone again
[/SIZE][SIZE=1][COLOR=#204a87](09:39:54 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#204a87]**Mitch:  **[/COLOR][/SIZE][SIZE=1]k
[/SIZE][SIZE=1][COLOR=#cc0000](09:40:15 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#cc0000]**Manos: **[/COLOR][/SIZE][SIZE=1][COLOR=#000000][FONT=Comic Sans MS]**change all the options to pulseaudio except the mixer**[/FONT][/COLOR][/SIZE][SIZE=1]
[/SIZE][SIZE=1][COLOR=#204a87](09:40:42 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#204a87]**Mitch:  **[/COLOR][/SIZE][SIZE=1]hrm
[/SIZE][SIZE=1][COLOR=#204a87](09:41:30 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#204a87]**Mitch:  **[/COLOR][/SIZE][SIZE=1]like it works for like 5 seconds after I force reload alsa
[/SIZE][SIZE=1][COLOR=#cc0000](09:41:47 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#cc0000]**Manos: **[/COLOR][/SIZE][SIZE=1][COLOR=#000000][FONT=Comic Sans MS]**this is a good sign**[/FONT][/COLOR][/SIZE][SIZE=1]
[/SIZE][SIZE=1][COLOR=#cc0000](09:41:56 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#cc0000]**Manos: **[/COLOR][/SIZE][SIZE=1][COLOR=#000000][FONT=Comic Sans MS]**we at least traced where the problem is**[/FONT][/COLOR][/SIZE][SIZE=1]
[/SIZE][SIZE=1][COLOR=#204a87](09:42:09 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#204a87]**Mitch:  **[/COLOR][/SIZE][SIZE=1]wait
[/SIZE][SIZE=1][COLOR=#204a87](09:42:12 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#204a87]**Mitch:  **[/COLOR][/SIZE][SIZE=1]it might be fixed
[/SIZE][SIZE=1][COLOR=#204a87](09:42:41 PM) [/COLOR][/SIZE][SIZE=1][COLOR=#204a87]**Mitch:  **[/COLOR][/SIZE][SIZE=1]no[/SIZE]


[SIZE=1]I really need sound. I am sick of no sound :( Please please help me. 
[/SIZE]


[SIZE=1]
[/SIZE]
 [SIZE=1]
[/SIZE]

---

### Post by P4man on 2009-09-15
It might help if you provided some basic info like what version of ubuntu you have, what soundcard, etc.

Completely wild guess: open a terminal and type:

```
alsamixer -c0
```

Move all relevant sliders up with arrow keys.

---

### Post by elliotn on 2009-09-15
Try this topic, comprehesive sound 

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Mitchcm on 2009-09-15
I got it fixed... but I didnt bookmark the site I got it off of... 

                                 mitch@ubuntu:~$ sudo alsaconf  
 sudo: alsaconf: command not found  
 mitch@ubuntu:~$ lsmod | grep intel  
                                   mitch@ubuntu:~$ sudo apt-get install module-assistant 

                                  mitch@ubuntu:~$ sudo module-assistant update 

                                  mitch@ubuntu:~$ sudo module-assistant prepare 

                                                                    mitch@ubuntu:~$ sudo module-assistant 



the I remember something about selecting build and install and I remember a screen with a bunch of other crap on it with alsa.... I cant remember I'm sorry i didnt bookmark it... but sitll. I put in only what I said becuase it was HUGE between. So if you want to full bit tell me :)

EDIT~~~~~~~

I found teh site!!

[http://ubuntuforums.org/showthread.php?t=1032795](http://ubuntuforums.org/showthread.php?t=1032795)

HOURS LATER AFTER ~~~~

I left my computer open as I went to go have diner with family and .... now the sound isnt working again :(

---

### Post by the mage on 2009-09-15
> **P4man said:**
> It might help if you provided some basic info like what version of ubuntu you have, what soundcard, etc.

Completely wild guess: open a terminal and type:

```
alsamixer -c0
```

Move all relevant sliders up with arrow keys.
I am Manos and here are some info...
He is using ubuntu 9.04, 

aplay -l gives him that :

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

### Post by P4man on 2009-09-16
> **the mage said:**
> I am Manos and here are some info...
He is using ubuntu 9.04, 

aplay -l gives him that :

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

there is another active thread with someone with the same problem on that same soundcard. If you know how, I would suggest trying to download and compile newest alsa, and/or enable the backport repository. Also worth checking if the problem is resolved in karmic. It seems that card doesn't work with jaunty and supplied alsa drivers.

---

