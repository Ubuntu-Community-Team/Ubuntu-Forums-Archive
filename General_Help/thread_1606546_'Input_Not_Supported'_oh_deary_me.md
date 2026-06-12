---
title: "'Input Not Supported' oh deary me"
date: 2010-10-26
forum: General Help
---

### Post by evilsoup on 2010-10-26
Ach! I've been using Ubuntu for about two years now, then suddenly today (after my PC accidently lost power) the screen resolution changed to 800x600 (it is, in fact, a widescreen monitor, and this resolution looked 'zoomed in'). The only two resolutions detected with xrandr were in the 4:3 ratio (800x600 and something worse). I followed some instructions, trying to reset the resolution to 1024x576.

I got as far as 

$ xrandr --newmode "1024x576" ...

then,

$xrandr --addmode default 1024x576

but when I 

$xrandr --output default --mode 1024x576

I a message to the effect of 'your screen can only support 800x600 or less'. *Ah-ha*, I thought, *you stupid machine; this screen has had a greater resolution for over a year*.

And so, from System->Preferences->Monitor, I forced the computer to switch to this new resolution. When prompted, I reset.


My current problem is that when I turn the computer on, the monitor displays a floating 'Input Not Supported' sign. I Ctrl+Alt+F1'd, and now all 'xrandr' and 'cvt' commands return: 

Can't Open Display


My first priority is to get the computer back to it's less-broken 800x600 state; any ideas (Thanks in advance)?

EDIT: I'm running Ubuntu 10.04

---

### Post by evilsoup on 2010-10-26
Bumpity-bumpity-bump.

I know it's pretty late, but... any ideas?

---

### Post by evilsoup on 2010-10-27
*Cough*

erm... anyone? This is kind of important.

---

### Post by Swagman on 2010-10-27
Run Recovery from Grub ?


Just answering so you can see you post has been seen !!

---

### Post by evilsoup on 2010-10-27
Thanks for the answer... this recovery from grub, it wouldn't affect stored files, would it? It's just that my backup hard-drive has broken(hasn't been a good few days), so I need to be very careful.

---

### Post by msandoy on 2010-10-27
You do not state witch distro you are using, only that you have been using Ubunto for two years. Guessing you have a slightly outdated version still using xorg.conf. You could edit /etc/X11/xorg.conf, and change the default screen size to 800 x 600.

---

### Post by evilsoup on 2010-10-27
I am running 10.04.

I have /etc/X11/xorg.conf open in nano right now (typing this on the laptop). I'll just copy the whole thing here:

```
Section "Screen"
       Identifier   "Configured Screen Device"
       Device "Configured Video Device"
       SubSection "Display"
              Virtual 2048 2048
       EndSubSection 
EndSection

Section "Device"
       Identifier   "Configured Video Device"
EndSection
```

Is it the '2048 2048' I should change?

(Also, I just tried booting from a live CD, it used a display of 1600x900; I suppose I have probably broken sonething mysterious).

---

### Post by Grenage on 2010-10-27
Personally, I'd just create a new xorg.conf from scratch.  There's a lot to be said for being able to actually 'see' and change settings (as convenient an background magic is).

---

### Post by stoneage on 2010-10-27
I couldn't say whether x is trying to use that resolution, but 2048 x 2048 is surely wrong. 

You could try renaming xorg.conf then reboot. If it doesn't fix it at least it won't do any harm as you can restore it.

Another option is 
```
sudo dpkg-reconfigure xserver-xorg
```


More info:-
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by evilsoup on 2010-10-27
> **stoneage said:**
> I couldn't say whether x is trying to use that resolution, but 2048 x 2048 is surely wrong. 

You could try renaming xorg.conf then reboot. If it doesn't fix it at least it won't do any harm as you can restore it.


Thank you, that fixed the graphical interface and reset it to 1600x900! I  suppose I must have done something to corrupt the xorg.conf, that was  probably the problem.

@ Grenage: I might do that, but first I'll read up on it a bit.

Thanks everyone!

EDIT: can someone tell me how to change the title to [solved] or could a mod do it?

EDIT2: okay, I got it.

---

### Post by Swagman on 2010-10-27
> **evilsoup said:**
> Thanks for the answer... this recovery from grub, it wouldn't affect stored files, would it? It's just that my backup hard-drive has broken(hasn't been a good few days), so I need to be very careful.

I see you have got the problem fixed.. Excellent.

Just for your knowledge and if this turns up on someone else's google search...

Recovery simply rescans your hardware and sets it back to how it was after your fresh install.

By that I mean drivers/settings. It doesn't touch personal files or installed programs.

---

