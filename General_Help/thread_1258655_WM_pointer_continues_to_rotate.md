---
title: "WM pointer continues to rotate"
date: 2009-09-05
forum: General Help
---

### Post by jheaton5 on 2009-09-05
I have had Jaunty on my laptop since it went to Beta.  I have had virtually no probllems with it.  A few days ago the mouse pointer did not change from the rotating circle to the arrow pointer.  I suspect that some process that loads at boot is hung in a never ending loop.

When I load an application, the mouse pointer behaves appropriately, but goes back to a rotating circle when I view the desktop.

```
top
```
Shows Xorg always at the top of the list of running processes.  It is only using 1% of the CPU but it is always there.

---

### Post by NoaHall on 2009-09-05
Hm.. What have done to change things recently?

And have you got a USB mouse or a PS/2?
And is your graphics card driver up to date?

---

### Post by jheaton5 on 2009-09-05
The only changes to the system have been the usual weekly updates.
I have a usb mouse on a cord
Graphics card driver is Nvidia 180

Edit:

Unplugging mouse and activating touchpad has no effect.

---

### Post by NoaHall on 2009-09-05
Try using "F5" on the desktop, see if anything changes.
Try using "killall nautilus" and then "nautilus"
Do you have a big background or lots of launchers on the desktop?

---

### Post by jheaton5 on 2009-09-05
<F5> has no effect
```
$ killall nautilus
$ nautilus
``` has no effect
I have a full screen background with no launchers.
I do have launchers on the panel.

Edit:

<ctrl><alt<backspace> has no effect.

---

### Post by NoaHall on 2009-09-05
On Jaunty, <ctrl><alt<backspace> no longer exists( although you can make it exist if you want) Now it's "alt + k + printscreen"

Try to remove the background (or use a lesser quality one) and see if anything changes.

The launchers are only on the panel, and not the desktop?

Are you mounting any drives ? (apart from the main, of course :D)

---

### Post by jheaton5 on 2009-09-05
> **NoaHall said:**
> On Jaunty, <ctrl><alt<backspace> no longer exists( although you can make it exist if you want) Now it's "alt + k + printscreen"[1QUOTE]I'll try that later

> Try to remove the background (or use a lesser quality one) and see if anything changes.I just tried that, I cannot get the background menu to activate with a right click.  I did change background photos several times this morning, but the problem existed prior to that.  I will try a re-boot and see if I can remove the background picture then.  I'll let you know what happens.

[QUOTE]The launchers are only on the panel, and not the desktop? Yes, the launchers are only on the panel.  I have the following launchers installed on panel (they have been that way for a long time):
Putty
Idle
GAdmin-RSYNC
MySQL browser
MySQL Administrator
O O Spreadsheet
O O Writer
Gedit
Terminal
Thunderbird
link to a spreadsheet template
Rdesktop link to remote office computer
Firefox 3.5
Google Earth
HPLIP
Network Manager applet
Power Manager
Volume Applet
Clock 2.26

> Are you mounting any drives ? (apart from the main, of course :D)None at the moment. I frequently use another drive on my laptop and a flash USB stick.  I always unmount these drives when I am done with them and I never shutdown with them mounted.

I am going now to reboot and will report back.

---

### Post by NoaHall on 2009-09-05
Hm.. What other applications are you running at boot? Gnome-Do, etc. Try disabling them.

Are you using compiz-fusion?

---

### Post by jheaton5 on 2009-09-05
Problem fixed:
After re-boot, I was able to remove the background screen.  The process stopped and I got my arrow pointer back.  I reactivated the background and I still have my pointer.
> **NoaHall said:**
> Hm.. What other applications are you running at boot? Gnome-Do, etc. Try disabling them.

I remember now that I modified the background picture that I use which is a seascape with Tux super imposed on it.  I think that the problem began about that time.

> Are you using compiz-fusion? Yes.

Thanks for your help.

---

