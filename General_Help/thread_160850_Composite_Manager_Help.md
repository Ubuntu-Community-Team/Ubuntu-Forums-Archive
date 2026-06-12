---
title: "Composite Manager Help"
date: 2006-04-15
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-04-15
I am trying to get composite manager to work. I have an ATI Radeon Xpress 200M. I am a this step:

> For Supported ATI Cards (ATI 9250's and below) in Dapper (as soon as Dapper gets Xorg 7):

Make it look like this:

Quote:
Section "Device"
Identifier "Generic Graphics Card"
Driver "radeon"
Option "AccelMethod" "EXA"
Option "AGPMode" "4"
Option "EnablePageFlip" "true"
Option "DDCMode"
Option "RenderAccel" "true"
Option "SubPixelOrder" "NONE"
Option "ColorTiling" "false"
EndSection
Do I need to do this ? And I skipped it and after installing xcompmgr transset and now I get this error:

> chris@ubuntu:~$ xcompmgr -cC & killall gnome-panel
[1] 5912
No composite extension
[1]+  Exit 1                  xcompmgr -cC
chris@ubuntu:~$ xcompmgr -fF & killall gnome-panel
[1] 5925
No composite extension

What should I do ?

---

### Post by xXx 0wn3d xXx on 2006-04-15
Does anyone know what I should do ?

---

### Post by mrazster on 2006-04-15
Well....I did it....but with nvidia card....and it works great...a little buggy but  OK.

So about your problem.....how about the obvious?!?!...Try to do it as the "Howto" tells you ...with allt the steps including modifying your xorg.conf...

The whole thing is based on the "composite manager"..if I'm getting it right ..that is. And by skipping the step you are refering to you're also skipping enabeling the composite support in xorg.conf.

---

### Post by engla on 2006-04-15
Right. Take the hint from the error message.

> Section "Extensions"
        Option "Composite" "true"
EndSection


---

### Post by bofphile on 2006-04-17
Masterchief, did you get composite manager to work ? I have the same graphic card and I'm interested to know if it's possible to enable this feature.

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=bofphile]Masterchief, did you get composite manager to work ? I have the same graphic card and I'm interested to know if it's possible to enable this feature.[/QUOTE]
Well, it was buggy and it looked horrible on my graphics card. The window manager was really messed up and so was the transparancy. I was in firefox and even though my terminal window was under my firefox one, it showed up on top of it. Don't try it unless you know what your doing (I obviously didn't :)). To disable it you will have to boot into recovery mode and then do:
> 
sudo nano /etc/X11/xorg.conf
and remove the composite manager lines that you added. Then save it and reboot into normal mode.

---

### Post by bofphile on 2006-04-19
Ok thanks for the feedback, I will not try this feature.

I have a question for you, since you own an ATI XPress 200M, you must have a laptop. I was wondering if you find your desktop rather slow compared to Windows XP. It doesn't seem as responsive, minimizing or switching windows is noticably slower than with Windows.

Thanks.

---

