---
title: "Ubuntu stuck at low resoultion. even with fresh install."
date: 2009-08-10
forum: General Help
---

### Post by gksudo on 2009-08-10
Hello,
The other night I shutdown my Ubuntu machine right before I went to sleep.
The next morning, I woke up, and booted up my Ubuntu machine.
Everything seemed fine until I got to the login screen. The resolution was way to low!
So I pressed the button on my monitor (22" inch Westinghouse) that took me to it's main menu. It said it was running at 1024 x 768. When in the past, ubuntu has ran in 1680 x 1050!
So I went ahead and logged in, and went to System,Prefrences, and Then Screen Resolution. So I clicked on the drop down box that should have let me selected to something higher. But all it has was 1024 X 768(which it was currently running) and below.(800 x 500, 640, 480,)
I then edited my x.org configuration file, not knowing what I was doing, bricked the system. So I tried to re-install Ubuntu. I dropped in the installation dvd and rebooted my computer.But when I got to the installating program, it was running at 1024 X 768! What is going on?
I'm now running on puppy linux to make this post. (Puppy linux is running fine on 1680 X 1050, Revealing that ubuntu is the problem.)
Any help would be much appreciated,
Thanks.

---

### Post by ajmorris on 2009-08-11
hi there,
after you 'bricked' your system as you say... you needn't have re-installed... however, whats done is done. As for your resolution, in ubuntu, please open up a terminal, and type the following:
 
```
sudo -i
``` #to become super user
```
xrandr -s 1680x1050
``` #to set the resolution to 1680x1050
 
If this doesnt work, please post the error output, along with the output of the following:
 
```
xrandr -q
``` This will list the resolutions avaliable to your current xorg session.
 
AJ

---

### Post by gksudo on 2009-08-12
Thanks! I'm glad to get back to Ubuntu now. :)

---

### Post by ajmorris on 2009-08-13
> **gksudo said:**
> Thanks! I'm glad to get back to Ubuntu now. :)
 
cool, glad it worked, if you need it permanently changed, so that it is that resolution upon subsequent reboots, just make sure that resolution is set in /etc/X11/xorg.conf 
 
AJ

---

