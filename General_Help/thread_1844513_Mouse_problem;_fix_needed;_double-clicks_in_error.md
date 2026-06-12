---
title: "Mouse problem; fix needed; double-clicks in error"
date: 2011-09-15
forum: General Help
---

### Post by Bladeforger on 2011-09-15
For the last two-three weeks my mouse has started interpreting about every other single click as a double click.  It's apparently a bug.  It's apparently a known bug.  It has apparently been a bug, off and on, since 2008 or 2009.  It doesn't affect all mice.

I have 9.10, Karmic Koala.  I went to the trouble, when I installed it, to also install kde3.5 so I could play the old goldrunner.  I don't know if an upgrade will leave my kde3.5 in place and the whole process basically kills a day of time.  Even though Karmic was only supported through April 2011, something has changed to break it.

So upgrading is the least palatable solution--if it even would solve the problem, which isn't guaranteed.  (Okay, going back to Windows is the LEAST palatable solution; but upgrading is still not the option I want to use... and it shouldn't be necessary.)

Buying a new mouse to fix a software problem is palatable, but it shouldn't be necessary.  I'll do it if I could know that would fix the problem.

I have a Gigaware wired optical mouse with USB interface.

I've seen one fix that changes clocksource to jeffries.  My clocksource is tsc, and jeffries isn't in the list of available clocksources.

Until the bug is fixed, there ought to be a decent workaround. Does anyone have a solution???

Keith

---

### Post by sanderd17 on 2011-09-15
There are not a lot of persons willing to help with a distro that has reached the end of life. The first question always is "does it happen too in the most recent release?"

Maybe you should not upgrade for your mouse, but you should upgrade for other reasons. So I see no point in trying to solve such a problem when it will probably be fixed with an upgrade.

---

### Post by Bladeforger on 2011-09-15
That's a valid statement; however, the problem is apparently not being cured with the later versions.  Here's a link to a thread with the same problem on Natty:
[http://ubuntuforums.org/showthread.php?t=1823912]("http://ubuntuforums.org/showthread.php?t=1823912")

Here's a post from 2010 without the version of Ubuntu identified but with a cogent explanation of what the poster thinks is the problem, i.e. "bounce"
[http://ubuntuforums.org/showthread.php?p=9574744]("http://ubuntuforums.org/showthread.php?p=9574744")

I found that the problem must go back to 2004, at least...
[http://www.linuxquestions.org/questions/linux-general-1/double-click-bug-171306/]("http://www.linuxquestions.org/questions/linux-general-1/double-click-bug-171306/")

I tried the xev program and watched the single-clicks versus double-clicks and did NOT get any single-clicks that appeared to be double-clicks--nor did I see two mice being referenced.  That was puzzling.  I did it about 30 times.

I'm not sure but think that would mean it's in the graphical environment somewhere.  The same problem happens if I log in with kde.  (Haven't tried the old kde 3.5 yet, but that's just there for one fun little program.)

The clunky workaround I've come up with is being deliberate with single-clicks... press down and wait half a second to a second and then release.  This usually works.  It's clunky.  I've gone into the mouse preferences and changed the double click timeout slider from short to long and everywhere in between.  I currently have it set to the longest setting.  For a double-click I use a single click + Enter where possible.  

Since this is a bug that repeats itself in various versions, I think it's a valid question to ask "What is a good workaround for when it happens?"  It's obviously not really being fixed in later versions, it just takes a while before people complain.

---

### Post by woolford on 2012-06-28
Looks like this problem has resurfaced, because I'm getting it in 11.10. I didn't have the problem when I first installed Ubuntu, it worked perfectly. So an update somewhere has re-introduced it.

Single click on the mouse is being received as a double click 80% of the time. Causes endless problems with highlighting text for copy/paste operations in editors.

My mouse is a Logitech Nano.

Anyone else seeing this problem?

---

### Post by ksian on 2012-06-29
Same problem here on Ubuntu 12.04 with a Logitech Performance MX mouse.

---

### Post by Seanlol on 2012-06-29
Could you guys post exactly which mice you're using? A few of you have written that you're using Logitech mouse; I use a Logitech M525 wireless laptop mouse on my Laptop's Ubuntu 12.04 partition, and I am not having this problem. Perhaps if you all post exactly which versions of Ubuntu and which mice you're using, it may become easier to see where the problem lies.

---

### Post by fuchsmi on 2012-07-01
same problem here.

Using 12.04 clean install on a Thinkpad X220. The internal mouse is mostly useless.

After a year I wanted to get back from Windows, but with this it will not happen...

hopefully there's a solution soon.

---

### Post by woolford on 2012-07-02
> **Seanlol said:**
> Could you guys post exactly which mice you're using? A few of you have written that you're using Logitech mouse; I use a Logitech M525 wireless laptop mouse on my Laptop's Ubuntu 12.04 partition, and I am not having this problem. Perhaps if you all post exactly which versions of Ubuntu and which mice you're using, it may become easier to see where the problem lies.

My mouse is a Logitech VX Nano cordless laser mouse for notebooks

[http://www.amazon.co.uk/Logitech-Cordless-Laser-Mouse-Notebooks/dp/B000U75V02](http://www.amazon.co.uk/Logitech-Cordless-Laser-Mouse-Notebooks/dp/B000U75V02)

Ubuntu version 11.10. Fully up to date.

---

### Post by codingman on 2012-07-02
This is a long shot, but try reinstalling your mouse driver, I don't have this problem with a mouse of logitech's newer models.

---

### Post by woolford on 2012-07-03
> **codingman said:**
> This is a long shot, but try reinstalling your mouse driver, I don't have this problem with a mouse of logitech's newer models.

Not sure how to do that in Ubuntu. I thought it used a generic mouse driver built into the kernel.
I haven't installed a specific driver for my mouse.

---

### Post by woolford on 2012-07-03
I think I've solved this mystery (for me anyway).
Some time ago I had problems after an update, which meant that Unity didn't start up. It was related to the graphics card (Nvidia). I used the /etc/X11/xorg.backup file.
However this deleted the section related to mouse device.

I added the following to my xorg.conf, which seems to have resolved the problem. Using xev I can see no repeated mouse click events

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

---

