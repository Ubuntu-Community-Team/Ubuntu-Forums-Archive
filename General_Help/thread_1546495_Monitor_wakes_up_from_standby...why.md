---
title: "Monitor wakes up from standby...why?"
date: 2010-08-05
forum: General Help
---

### Post by titomax82 on 2010-08-05
Hi all,
I do not have a keybord button to turn my monitor off, so I made this luncher
"xset dpms force off"
but after a variable time (from few seconds to 2 minutes) monitor wakes up automatically, even if i don't touch any key or move mouse... i suspcted my usb mouse could have some "auto movements" so i detached it, but nothing changes....monitor continue to wake up without a reason....any suggestion?

(ubuntu 10.04 - the same with xset dpms force suspend or standby)

---

### Post by utilitytrack on 2010-08-06
try it

```
xrandr --output LVDS1 --off

```

---

### Post by titomax82 on 2010-08-06
try as a substitute for my launcher? then...does it wake up touching mouse or keyboard?

i tried it in the console...: warning: output LVDS1 not found; ignoring

---

### Post by utilitytrack on 2010-08-06
No, don't worry, your display will not wake up never :)

This is strange if you work on laptop:
[FONT="Courier New"]> warning: output LVDS1 not found; ignoring[/FONT]
Ok, give here
```
xrandr
```
and
```
xrandr -v
```

---

### Post by inameiname on 2010-08-06
None of those commands will work, at least from my research. This is the only one that works under Lucid. And this is after a yr of hardore looking into your issue. Just make script and add this (save in text file and set as executable) and make launcher direct you to its location:


```

#!/usr/bin/python

import time
import subprocess
from Xlib import X
from Xlib.display import Display

display = Display(':0')
root = display.screen().root
root.grab_pointer(True,
        X.ButtonPressMask | X.ButtonReleaseMask | X.PointerMotionMask,
        X.GrabModeAsync, X.GrabModeAsync, 0, 0, X.CurrentTime)
root.grab_keyboard(True,
        X.GrabModeAsync, X.GrabModeAsync, X.CurrentTime)

subprocess.call('xset dpms force off'.split())
p = subprocess.Popen('gnome-screensaver-command -i'.split())
time.sleep(1)

while True:
    print display.next_event()
    p.terminate()
    break

```

---

### Post by utilitytrack on 2010-08-06
> **inameiname said:**
> None of those commands will work, at least from my research.

About which commands do you speak?

---

### Post by inameiname on 2010-08-06
The "xset dpms force off" and any of it's variations. 

Yours works of course, though it must be attached to a button to turn off as well, otherwise you must restart your computer entirely to get the display back on. And not sure if it's for non-laptops. Though, a quick push of the monitor button does that. :P

Here is a good thread, one of many, about this:

[http://ubuntuforums.org/showthread.php?t=1317747](http://ubuntuforums.org/showthread.php?t=1317747)

Guess in all, there are options.

---

### Post by titomax82 on 2010-08-07
xrandr:
Screen 0: minimum 320 x 240, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       50.0* 
   1024x768       51.0  
   960x540        52.0  
   840x525        53.0  
   800x600        54.0  
   800x512        55.0  
   720x450        56.0  
   680x384        57.0     58.0  
   640x512        59.0  
   640x480        60.0     61.0  
   576x432        62.0  
   512x384        63.0  
   400x300        64.0  
   320x240        65.0  

xrandr -v:
xrandr program version       1.3.2
Server reports RandR version 1.3


i'm gonna try the script...

---

### Post by titomax82 on 2010-08-07
[inameiname]("http://ubuntuforums.org/member.php?u=949055") ... i'm so noob on linux (only 3 weeks of experience)... can you help me making the script step-by-step?

---

### Post by inameiname on 2010-08-07
Sure...lucky I happen to be bored and awake at this hour. :P

Okay, just right click in nautilus, the file browser, click 'Create Document" > select "Empty File" and then name it something. Then copy and paste all that I wrote. Then when saved that text file, right click it, and click on "Properties". Then go to "Permissions" and click "Allow executing as program". This is how to do it.

To make it much easier for you, which I should've done to begin with, I'll just attach the script for you and that's that. You may have to do the click "Allow executing as program" though, but that's all. 

Then when you run the script, it'll turn screen off. All you have to do then is hit a button or move touchpad when you want the screen to return.

And to create a launcher, just direct where the script is. Personally, I keep a launcher on my taskbar next to the start button, and this is where mine is and what is in the launcher:

/home/me/.gnome2/nautilus-scripts/My_Scripts/Display-Off/Display-Off.py

---

### Post by titomax82 on 2010-08-07
when I double click on the file (permission allowed...)...it does nothing (in any case: execute in terminal or simply "execute")

---

### Post by titomax82 on 2010-08-07
i tried to run from terminal:

/home/gtm/Scaricati/Display-Off.py
Traceback (most recent call last):
  File "/home/gtm/Scaricati/Display-Off.py", line 5, in <module>
    from Xlib import X
ImportError: No module named Xlib




maybe I need some package?

---

### Post by inameiname on 2010-08-07
When you double click on the python script that I attached, prior to marking it as executable as I mentioned, it'll open up like any old text document in gedit. If you double click to open it after marking it as executable, it should pop up a little box that asks you if you what to "open in terminal", "run" or "execute", or "display" it. You want to "run" it.  

Not sure what might be your issue.

---

### Post by inameiname on 2010-08-07
Hmmm, your readout is interesting. Not sure what to tell you. Uhm, you shouldn't need to install anything else to make it work, as python and it's extras should already be installed under a normal Ubuntu installation as default. 

This is my readout through the terminal:

~ /home/me/Temp/Display-Off.py
Xlib.protocol.request.QueryExtension
Xlib.protocol.event.KeyRelease(event_y = 550, state = 0, type = 3, child = <Xlib.display.Window 0x03a002a9>, detail = 36, window = <Xlib.display.Window 0x00000103>, same_screen = 1, time = 7541463, root_y = 550, root_x = 694, root = <Xlib.display.Window 0x00000103>, event_x = 694, sequence_number = 10)

So it seems something on your computer isn't working, or isn't installed if you are getting that readout. 

Try this:

sudo apt-get install python-xlib

It is installed on mine, so maybe if it isn't on yours, there lies the issue.

UPDATE:

Actually, I think your issue is indeed not having "python-xlib" installed. I just realized it was something I had to install after, and not something that comes by default.

---

### Post by titomax82 on 2010-08-07
phyton-xlib was missing, now it works perfectly! thanks inameiname!!!!

can you take a look here? [http://ubuntuforums.org/showthread.php?t=1541620](http://ubuntuforums.org/showthread.php?t=1541620)

---

### Post by inameiname on 2010-08-07
Sweet, glad it works for ya.

As far as your webcam issue, I'm not really sure what is up with it. On my laptop that I'm using, cheese also puts out USB 2.0 Camera for my built-in one as well. Mine's under /dev/video0. But mine worked from the get-go. Not sure why yours isn't under Cheese or any of the others. Sounds to me like a tweaky/faulty driver for it, as the apps pick it up as being there, but some part of it is just not being correctly read. You may be right that it's a kernel issue, or just a graphics driver issue, idk. Can't really tell you for sure what's the matter, sorry. Obviously, the fact that it doesn't show a picture in all of those apps you mentioned tells you it's not application-specific. 

Not sure if this relates to your issue at all, but I've noticed that sometimes with my USB tv tuner, it's being read as /dev/video1, and thus, I must change all the apps I use it in to /dev/video1, instead of the default /dev/video0, because of my built-in webcam, and for some of the apps out there, I have yet to find a way to do that. Anyway, perhaps for some odd reason your webcam is /dev/video1 and what is being supposedly picked up is something that is in the /dev/video0, which could be something else built-in to yours, idk. Though, forgive me if this is way off or not even close. It's nearly 7AM here and I'm nearly about to fall asleep. :P

You could try a newer kernel or something and see if that fixes things. I'm guess as a newbie you are using the latest kernel that is available in the official repos, which should be I believe 2.6.32-24. If you want to try the absolute latest kernel, which has tons more fixes than that one, install this PPA repo. Oh, and if for some reason it doesn't work, you can always revert back to your old one, and remove this one. You'd just have to restart and in the boot menu choose the older one.

In the terminal:

sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
sudo aptitude install linux-headers-2.6.35-14-generic linux-image-2.6.35-14-generic

---

### Post by titomax82 on 2010-08-07
mm..no...there's only dev/video0 and in programs is seen correctly as dev/video0

however..thanks again for this solved thread :)

---

### Post by inameiname on 2010-08-07
Again, not a prob. Try the updated kernel. As you said it worked fine with older Ubuntu versions, so maybe there was a regression or something with the Lucid kernel. If want to, of course. Just remember to restart so it starts using the newest kernel.

---

### Post by titomax82 on 2010-08-07
i do not know how to test other kernel versions....but it seems something complicated and dangerous... :)

---

### Post by inameiname on 2010-08-07
It can be. From my experience, so long as you don't remove your old one, you can always revert back to it.

Basically, if you input those three commands I mentioned, it'll add that kernel to your computer as an option on boot. You have the choice of booting with it, or with your current one, however as a higher number, it will be the default one over your current one at boot. It shouldn't hurt your computer at all, outside of maybe a chance of not running right at first boot or issues later on, idk. Usually they make it better. Regardless, if something doesn't work, a reboot and before it boots, hit "Shift key" (might be ESC, I can't remember), and you can choose which to boot with. That's all. 

And I use Startup-Manager to change which will autoboot at startup:

sudo apt-get startupmanager

And I use Ubuntu-Tweak to remove the kernel(s) that are not wanted anymore as I like it better than the terminal way:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Guess with all of that, it does sound complicated. :P

---

### Post by titomax82 on 2010-08-07
I continue on the appropriate thread...

---

### Post by snoxu on 2011-07-05
sorry please delete

I meant to post about the same issue here:
[http://ubuntuforums.org/showthread.php?t=1317747](http://ubuntuforums.org/showthread.php?t=1317747)

---

