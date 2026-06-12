---
title: "Touchpad works, except...."
date: 2009-12-03
forum: General Help
---

### Post by edpatterson on 2009-12-03
The disable touchpad while typing option has not functioned since I upgraded to 9.10. I found a help file that said to edit the 'input device' section of my xorg.conf file but my xorg.conf file does not have an input device section.

I had no idea how often my pudgy hand bumped the touchpad.

Any and all help appreciated.

Ed

---

### Post by oldgeekster on 2009-12-03
> **edpatterson said:**
> The disable touchpad while typing option has not functioned since I upgraded to 9.10. I found a help file that said to edit the 'input device' section of my xorg.conf file but my xorg.conf file does not have an input device section.

I had no idea how often my pudgy hand bumped the touchpad.

Any and all help appreciated.

EdEd, the search function here is your friend - you didn't mention what kind of system/touchpad you have but if you just do a search for "touchpad" I'll bet you find a solution for your particular system.  For instance, on my 3 year old Toshiba Satellite, I was tickled to find that I could turn off the touchpad by simply holding down the Fn key and tapping the F9 key. Of course doing it again turns it back on.:popcorn:

Hope this helps!

---

### Post by Zorael on 2009-12-03
One workaround is to use xinput for this.

For a Synaptics touchpad, the command would be;
```
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 0
```
You would have to make a script of this and have it run upon login.

On a sidenote, newer Synaptics drivers (Karmic) have an option to enable palm detection, to avoid accidental taps when typing. Long list incoming; scroll down.
```
$ xinput list-props "SynPS/2 Synaptics TouchPad"
Device 'SynPS/2 Synaptics TouchPad':                          
        Device Enabled (97):    1                             
        Synaptics Edges (243):  1752, 5192, 1620, 4236        
        Synaptics Finger (244): 24, 29, 255                   
        Synaptics Tap Time (245):       180                   
        Synaptics Tap Move (246):       221                   
        Synaptics Tap Durations (247):  180, 180, 100         
        Synaptics Tap FastTap (248):    0                     
        Synaptics Middle Button Timeout (249):  75            
        Synaptics Two-Finger Pressure (250):    280           
        Synaptics Two-Finger Width (251):       7             
        Synaptics Scrolling Distance (252):     100, 100      
        Synaptics Edge Scrolling (253): 1, 0, 0               
        Synaptics Two-Finger Scrolling (254):   0, 0          
        Synaptics Move Speed (255):     0.400000, 0.700000, 0.009952, 40.000000
        Synaptics Edge Motion Pressure (256):   29, 159                        
        Synaptics Edge Motion Speed (257):      400, 800                       
        Synaptics Edge Motion Always (258):     0                              
        Synaptics Button Scrolling (259):       1, 1                           
        Synaptics Button Scrolling Repeat (260):        1, 1
        Synaptics Button Scrolling Time (261):  100
        Synaptics Off (262):    0
        Synaptics Guestmouse Off (263): 0
        Synaptics Locked Drags (264):   0
        Synaptics Locked Drags Timeout (265):   5000
        Synaptics Tap Action (266):     0, 3, 0, 0, 1, 2, 3
        Synaptics Click Action (267):   1, 1, 1
        Synaptics Circular Scrolling (268):     0
        Synaptics Circular Scrolling Distance (269):    0.100000
        Synaptics Circular Scrolling Trigger (270):     0
        Synaptics Circular Pad (271):   0
        **[COLOR="Green"]Synaptics Palm Detection (272): 1[/COLOR]**
        Synaptics Palm Dimensions (273):        10, 199
        Synaptics Coasting Speed (274): 45.000000
        Synaptics Pressure Motion (275):        29, 159
        Synaptics Pressure Motion Factor (276): 1.000000, 1.000000
        Synaptics Grab Event Device (277):      1
        Synaptics Gestures (278):       1
        Synaptics Capabilities (279):   1, 1, 1, 1, 1
        Synaptics Pad Resolution (280): 110, 100
        Synaptics Area (281):   0, 0, 0, 0
```
```
xinput set-int-prop "SynPS/2 Synaptics TouchPad" **[COLOR="Green"]"Synaptics Palm Detection"[/COLOR]** 8 1
```

I have this script in my KDE autostart directory to enable palm detection, disable two-finger scrolling, raise edge motion speed (the speed at which the cursor continues to move when you drag an object and hit the pad edge), and enable coasting (to make it continue scrolling when you "flick" your finger).
```
#!/bin/bash

echo Setting preset Synaptics options

echo - palm detection...
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Palm Detection" 8 1

echo - two-finger scrolling...
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 0 0

echo - edge motion speed...
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Motion Speed" 32 400 800

echo - coasting speed...
xinput set-float-prop "SynPS/2 Synaptics TouchPad" "Synaptics Coasting Speed" 45
```
On older installations (Jaunty and so forth) not all these options are available, but if so it'll only complain and do nothing; it won't break anything.

---

### Post by edpatterson on 2009-12-03
You are right, it is my friend and I did use it. It found all kinds of instances of the touchpad not working at all after an upgrade and only the one for changing it's behaviour without using the gui.

I have an actual button I can press to enable/disable the touchpad but that would become a major pain. I would much prefer the automatic disabling it for 2 to 5 seconds when I begin to type.

Ed

Oh, yeah
HP Pavilion dv6000

I started with version 8 and have upgraded every time one became available. I believe it has a Synaptic touch pad, there is of course no name on it :-)

---

### Post by edpatterson on 2009-12-03
> **Zorael said:**
> One workaround is to use xinput for this.

I use gnome, would I have to somehow disable the existing touchpad support then find a gnome compatible script?

It worked fine before the upgrade so I was hoping someone would already have found the solution and post it here.


Ed

---

### Post by oldgeekster on 2009-12-03
> **edpatterson said:**
> You are right, it is my friend and I did use it. It found all kinds of instances of the touchpad not working at all after an upgrade and only the one for changing it's behaviour without using the gui.

I have an actual button I can press to enable/disable the touchpad but that would become a major pain. I would much prefer the automatic disabling it for 2 to 5 seconds when I begin to type.

Ed

Oh, yeah
HP Pavilion dv6000

I started with version 8 and have upgraded every time one became available. I believe it has a Synaptic touch pad, there is of course no name on it :-)Ayup, it is a Synaptics Touchpad, and most of the problems I initially read in the forums last month about it were centered around their touchpad simply not working.

Like you, I simply want the provided Gnome widgets to work in the expected manner. (i.e. Mouse Preferences | Touchpad | Disable touchpad while typing) - dang thing "should" work but in many cases didn't and I sure as heck wasn't implying that it shoudn't. (My own doesn't, thus the "workaround" using Fn+F9 for mine or your case the button).

Since you, (like I), chose the "upgrade" path to get to Karmic - I would be willing to bet this problem would go away with a fresh "clean" install of Karmic.  If, during upgrade, you (like I) chose to not let it update your grub menu.lst file, (see [this post]("http://ubuntuforums.org/showpost.php?p=8430812&postcount=29")), it can cause one to be pointing to an older kernel - which can create a ton of "unexpected" problems in Karmic. (Just took a look at my own  /boot/grub/menu.lst which appears to be OK).

I will be doing a hard drive replacement/upgrade on this notebook this month, and plan to do a clean 9.10 install at that time.  Will try to remember to let you know if I still can't suspend my keypad while typing afterward. ;)

Regardless of the OS - it has always been my "policy" to do clean installs rather than upgrades - every time I have violated that I am reminded of the old saw "That way there be dragons!"......

---

### Post by edpatterson on 2009-12-04
Well, I just tried the install and script for [here]("https://help.ubuntu.com/community/SynapticsTouchpad"), no luck. My palm still reeks havoc. You have no idea how frustrating this is.

I've spent better than a year getting everything 'just right' and I really do not want to start all over.

Ed

---

### Post by sgosnell on 2009-12-04
You can install touchfreeze, it's in the repositories.  Or you can add a section to your xorg.conf as follows:
```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "synaptics"
    Option        "SHMConfig" "true"
EndSection

```
Then run ```
syndaemon -d -i 1
``` at startup.  You can do that by creating a new launcher in System/Preferences/Startup Programs, with that as the command, naming it whatever you like.  Syndaemon is my choice.  You can change the 1 to whatever number you want, it's the number of seconds the touchpad is disabled after a keypress.  One second is enough for me, but you can make it higher if you want, it doesn't even have to be an integer, you can make it 1.5 seconds if you want.

---

### Post by edpatterson on 2009-12-04
I installed touchfreeze. It showed up in the the launcer bar. I opened it, set the delay to 2 seconds, clicked apply, No change. Fat hands still cause me grief.

I tired the syndaemon -d -i 5 Same thing, touchpad is still active. I 1 2 3 4 and 5 second delays, no differnece. ps aux showed 8 differenc syndaemon processes.

Is it possible to back out the version 9 upgrade?

Where is xorg.conf? I tried a 'which xorg.conf' nothing. I then checked in /etc, notta. I am rapidly exhausting my knowledge, or lack there of.

Ed

---

### Post by sgosnell on 2009-12-04
/etc/X11/xorg.conf should be the location.  You need to add the synaptics section to it and reboot.  Obviously you have to edit as root or superuser.

I just noticed that you're on 9.10.  That may not use xorg.conf, I don't know.  Maybe someone who does know will be along soon.

OK, [this thread](http://ohioloco.ubuntuforums.org/showthread.php?p=8416788) seems to indicate that in Karmic the touchpad can be disabled for .5 seconds via System/Preferences/Mouse, by checking the appropriate checkbox.  See if that works for you.  Running touchfreeze from a console as root makes it work correctly in 10.04 rc, and the .5 second timeout seems to work correctly.  I still don't know how to set a longer delay, but I should find it through Google eventually.

Another update:  Just running syndaemon from a terminal seems to work in Lucid.  Have you tried that in Karmic?  If it does work, you should be able to run it at boot through System/Preferences/Startup Applications.

---

### Post by sgosnell on 2009-12-07
Try [this thread](https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig).  I had forgotten about this information, but it's probably the reason it's not working for you.  Starting with 9.04, hal does the work, and you need to set things there, not in xorg.conf.  Sorry for not remembering this earlier.

---

### Post by oldgeekster on 2009-12-07
> **sgosnell said:**
> Try [this thread]("https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig").  I had forgotten about this information, but it's probably the reason it's not working for you.  Starting with 9.04, hal does the work, and you need to set things there, not in xorg.conf.  Sorry for not remembering this earlier.THANK YOU!=D> I added the shmconfig.fdi file with the content recommended on that page, rebooted and, with SHMConfig enabled, now the touchpad appears to be disabled for about a second or so with each keystroke! (Following "System | Preferences | Mouse | Touchpad | Disable touchpad while typing" in the expected manner)...

I will need to test it a little further, but am having no difficulty typing this response even though the touchpad is enabled. :D

Hopefully, when Ed tries this fix he can add [SOLVED] to the title of this one.:cool:

---

