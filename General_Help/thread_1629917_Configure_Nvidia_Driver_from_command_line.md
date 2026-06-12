---
title: "Configure Nvidia Driver from command line"
date: 2010-11-24
forum: General Help
---

### Post by eakergd on 2010-11-24
Ubutntu 10.04 with latest Nvidia drivers from the Ubuntu repository.

My daughter just broke her laptop screen.  I can order another LCD - no problem, but until then she wants to use an external monitor.  With Windows, this used to be no big deal, because I would hook up a monitor, hit a key combo on the keyboard, and everything would come up on the other monitor.

I know how to do this using the GUI, but unfortunately, I can only see about a 2 inch strip at the top of her computer.  I can see the gnome menu bar, and when I go into the Nvidia configuration, I can't make out anything below the tops of the two monitors it detects. (I was able to get it to detect both displays, but I can't see to press the "configure" button.)

What I need to do, is configure the new monitor from the command line using the two inches of visible monitor that I have at the top of her broken LCD.  Can anyone walk me through the process or tell me what file I need to modify?

Thanks

---

### Post by endotherm on 2010-11-24
well first things first: backup your xorg.conf
```
sudo cp /etc/X11/xorg.conf   /etc/X11/xorg.conf.bu.20101124.0
```

nvidia-xconfig is the utility that the nvidia drivers use to configure X. 
try running it, and rebooting to restart X, and see where that leaves you.

---

### Post by eakergd on 2010-11-24
OK, I did that.  Gave some type of error that the default monitor was defined as "null" in xorg.conf, but it saved a backup of the file and said it rewrote a new one.  After restarting, I still only have a picture on the bad LCD.

---

### Post by efflandt on 2010-11-24
For nvidia, DFP (display flat panel) usually refers to the laptop display or DVI/HDMI.  CRT refers to VGA (even if you have LCD).

The laptop display is likely DFP-0 and the external display is likely CRT-1 if VGA or DFP-1 if DVI or HDMI.

So in the Screen or Device section of /etc/X11/xorg.conf try:

```
Option "UseDisplayDevice" "CRT-1"
```or "DFP-1" if a digital connection.

The only laptop I have with nvidia is an old one.  Half of its display on a diagonal is dark and the rest lags something awful due to whatever is broken.  I was able to see enough to use the gui to switch it to external display, but cannot see CMOS setup or grub menu.

---

### Post by eakergd on 2010-11-24
OK, I'll try that.

---

### Post by eakergd on 2010-11-24
Nothing doin' -- didn't work.

It has a section for Monitor where it names the device "Monitor0" and then in the screen section it tells it to use Monitor0.  Think it would help to copy and paste the monitor section and name a device "Monitor1" and then in the screen section tell it to use "Monitor1"?  I would just do it, but I'm afraid it would break it worse than it is.

Oh, I just thought of another thing -- would it be easier to configure remote access from the command line?  If so, I could just do that, and then remote in with one of my other laptops to configure the screen output for the broken one.

---

### Post by endotherm on 2010-11-24
> **eakergd said:**
> Nothing doin' -- didn't work.

It has a section for Monitor where it names the device "Monitor0" and then in the screen section it tells it to use Monitor0.  Think it would help to copy and paste the monitor section and name a device "Monitor1" and then in the screen section tell it to use "Monitor1"?  I would just do it, but I'm afraid it would break it worse than it is.

Oh, I just thought of another thing -- would it be easier to configure remote access from the command line?  If so, I could just do that, and then remote in with one of my other laptops to configure the screen output for the broken one.
good call
you can install ssh with this line:
```
sudo apt-get install openssh-server
```

or if you wish to turn on ubuntus "remote desktop" (vino/vnc), check this tread (a little aged byt should still work)
[http://ubuntuforums.org/showthread.php?t=266981](http://ubuntuforums.org/showthread.php?t=266981)

---

### Post by DarthScape on 2010-11-24
> **endotherm said:**
> good call
you can install ssh with this line:
```
sudo apt-get install openssh-server
```

or if you wish to turn on ubuntus "remote desktop" (vino/vnc), check this tread (a little aged byt should still work)
[http://ubuntuforums.org/showthread.php?t=266981](http://ubuntuforums.org/showthread.php?t=266981)

+1 to installing ssh

If you can VNC into it, you can change all of the video settings.

---

### Post by eakergd on 2010-11-30
Well, I finally had some more time to work on this.  Turns out SSH was the way to go.  I got in through SSH and enabled the remote desktop.  Connected to that and set up twinview in nvidia-settings. I tried to get nvidia-settings to pass directly through the SSH tunnel, but for some reason when I invoked nvidia-settings while logged on to the remote machine, it still pulled up the nvidia config from my computer (even though I had used the -X option when I started SSH).  That was frustrating, because the remote desktop viewer in ubuntu SUCKS!  I had to consistently disconnect and reconnect just to get a screen refresh.  Maybe there is some other way to force a refresh, but it wasn't obvious.

Anyway, mission accomplished.  My daughter has a working computer until the new LCD screen gets here.  Thanks for the help.

---

