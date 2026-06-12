---
title: "gpointing-device-settings"
date: 2010-05-22
forum: General Help
---

### Post by FERdeBOER on 2010-05-22
Hi all,

I have a little problem with gpointing-device-settings: on the circular displacement option, I select the right box to activate this command (photo 1) but, after restart, the program is again with the default option (all corners, photo 2).

I don't know what to do to solve this. :confused:

Thank you in advance.

---

### Post by timmyhiggy on 2010-05-31
I can confirm that I am also having this problem on my UNR 10.04. It leaves me with a very hard to use mouse for the first minute of starting my computer, and I have to change it every boot!

---

### Post by timmyhiggy on 2010-06-01
I'm just going to give this a mini bump as it has fallen to the bottom of the threads and will never be looked at otherwise!

---

### Post by alfbar1 on 2010-06-30
same problem any ideas?

---

### Post by FERdeBOER on 2010-06-30
Just found this:

[http://ubuntuforums.org/showthread.php?t=1400264](http://ubuntuforums.org/showthread.php?t=1400264)

I will try, maybe is the solution...

---

### Post by bobcollard on 2010-06-30
> **FERdeBOER said:**
> Just found this:

[http://ubuntuforums.org/showthread.php?t=1400264](http://ubuntuforums.org/showthread.php?t=1400264)

I will try, maybe is the solution...
Good luck getting gsynaptics working with 10.04.  My solution is to place gpointing-device-settings in startup applications and change it each restart or startup.

---

### Post by FERdeBOER on 2010-07-01
It works for me with no problems at all.
Ubuntu 10.04 64bits.

Three restarts and the circular scrolling option remains as I selected it.

A question to moderators: as is not a solution for gpointing-device-settings and seems that gsynaptics doesn't work for everybody... I shouldn't check this as solved, should I?

---

### Post by rp88 on 2010-08-16
To fix this issue of the circular scrolling settings not sticking after reboot on newer versions of ubuntu such as lucid and meerkat, gsynaptics wont work anymore since its replaced with gpointing-device-settings. Also synclient should not be used as it is depreciated. To fix it you must do the following:

Go to terminal and type in "xinput list" without the quotes. Then find the device that's your touchpad. Here is my output as an example:

[COLOR="DarkRed"]
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Broadcom Corp                           	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Broadcom Corp                           	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=13	[slave  keyboard (3)]
[/COLOR]

My touchpad is listed as "SynPS/2 Synaptics TouchPad" just find your touchpad and make note of its proper name.

Now invoke: [COLOR="DarkRed"]xinput set-prop "%s" --type=int "Synaptics Circular Scrolling" 1[/COLOR] and replace where I've typed %s with your proper touchpad name (make sure the proper touchpad name has quotes surrounding it) You may also use the id number instead of the proper name but the id number may change.

Now invoke: [COLOR="#8b0000"]xinput set-prop "%s" --type=int "Synaptics Circular Scrolling Trigger" 2[/COLOR] Again make sure you replace %s with your proper touchpad name. Also replace the number 2 at the end with the location you would like the circular scrolling to work with: 

[COLOR="#8b0000"]0	All Edges
1	Top Edge
2	Top Right Corner
3	Right Edge
4	Bottom Right Corner
5	Bottom Edge
6	Bottom Left Corner
7	Left Edge
8	Top Left Corner

[/COLOR]

To make the changes apply permenently: create a blank file and add the following to the first line (without quotes): "#!/bin/sh" and insert the two commands you invoked to enable circular scrolling and set circular scrolling position. Save the file anywhere you'd like. Mine is here ~/.config/CustomTouchpadSettings.sh just make sure it has a .sh extension and make it executable. Then go to startup applications and add that file to startup.

If you'd like to further customize your mouse and find that gsynaptics-device-settings isnt saving the settings across reboot then you can take a look at this article and follow the steps above, replacing "Synaptics Circular Scrolling Trigger" or "Synaptics Circular Scrolling" with the property you would like to change. List of properties and setting explanations can be found here: [http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html](http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html)

I've attached my file as an example. Also I'd like to thank "Mr. Picklesworth" here on ubuntu forums for some of the information that helped me accomplish this.

---

