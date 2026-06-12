---
title: "My monitor is capable of a higher resolution than 1024x768 but 1024x768 is the limit?"
date: 2009-07-10
forum: General Help
---

### Post by ceezy10 on 2009-07-10
yea so my monitor is cabaple of a 1280x1152 resolution. Yet the maximum resolution i can have in ubuntu is 1024x768. I tried a few terminal commmands no success. Maybe i used the wrong commands. I'm wondering how i can increase my screen resolution. 
Thank you 
and sorry for sounding or being a noob

---

### Post by philcamlin on 2009-07-10
system > prefrences >display and change it there??

---

### Post by ceezy10 on 2009-07-10
> **philcamlin said:**
> system > prefrences >display and change it there??
I tried that and this is why im posting this thread. when  i go to the display preferences it limits me to 1024 x768 resolution even though on windows and fedora my screen resolution can be higher

---

### Post by brookie on 2009-07-10
System > Preferences > Screen Resolution in Intrepid 8.10
give it a shot
if it doesn't work you may need to edit your xorg.conf file
more on that later if you need it
cheers,
brook

---

### Post by j.bell730 on 2009-07-10
Do you have your graphics drivers installed? I can just go into the nvidia control panel, which was installed with the nvidia drivers, and change it there. It offers me the option of 1280x1024 (my correct resolution).

---

### Post by ceezy10 on 2009-07-10
> **j.bell730 said:**
> Do you have your graphics drivers installed? I can just go into the nvidia control panel, which was installed with the nvidia drivers, and change it there. It offers me the option of 1280x1024 (my correct resolution).
haha well the thing is this workstation is a custom build given to me by my neighbor. I know the specs of the machine except for what graphics card it has in it. I could never quite find that out.

---

### Post by Legace on 2009-07-10
Post contents of **/etc/X11/xorg.conf**

---

### Post by lobner on 2009-08-06
I had the exact same problem with my screen!

I was all the way around to installing new drivers, and reverting to older drivers, and configing a xorg.conf with lots of funny stuff. None of it was working out.
But it seems I was going around the forrest, so to speak. The solution is quite simple with a ~/.xprofile file and use of xrandr.

See complete wiki solution about it here: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

