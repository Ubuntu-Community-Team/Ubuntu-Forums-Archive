---
title: "Single mouse click registering as double click"
date: 2010-03-13
forum: General Help
---

### Post by HoboJ on 2010-03-13
About a week ago I installed some updates. What they were I don't remember. After I did that my mouse started acting up. Now about half the time when I single click it registers as a double click. Also when I click and drag to select text anywhere it'll randomly do another click screwing up that process. 

So far I think the problem is when I press the left mouse button it registers the left click and then when I release, it randomly registers another left click. 

The mouse itself works fine if I take it to another PC that's using windows. 

OS: Ubuntu 9.10 64bit
Mouse: Microsoft Intellimouse 3.0

---

### Post by falconindy on 2010-03-13
Windows uses accidental double click detection -- something I'm not sure is available in Gnome. How does the mouse behave on another Ubuntu install (even a liveCD)?

---

### Post by 2hot6ft2 on 2010-03-13
You can enable/disable single/double click by opening a folder and clicking on Edit > Preferences > Behaviour there you will see
Single click to open items
Double click to open items

Pick the one you want it to do.
Maybe that will solve your issue.

---

### Post by HoboJ on 2010-03-13
> **falconindy said:**
> Windows uses accidental double click detection -- something I'm not sure is available in Gnome. How does the mouse behave on another Ubuntu install (even a liveCD)?

Mouse is perfect under an Ubuntu LiveCD. So something is changed between a default install and an updated install that causes this. I've also tried another mouse, it's an ancient ps/2 IBM mouse, it works fine with no issues but I wont be caught dead using it beyond just testing :) Any other ideas?

---

### Post by Poptart on 2010-03-18
I'm having the same problem, and it's happening with different mice. Changing the options to single/double clicking doesn't fix the problem for me because I do a lot of work in GIMP, and clicking to drag and then having the program click again in the middle of a drag screws up practically every tool you could use. :(

I can't resize windows or drag them around the desktop, either. I've tried fiddling with all sorts of mouse options to no avail, but I'm really not a hardware guru.

If anyone has any ideas I'd also be very appreciative!

---

### Post by Mike-dev-random on 2010-03-22
I'm seeing the same problem intermittently, 10-30% of the time. 

Examples:

selecting text suddenly starts over while I am dragging across it.

Moving a gnome-terminal causes it to maximize (acts like double click)

I am running 9.10 and fully up to date as of today, March 22nd.  The update it started with included the 2.6.31-20-generic kernel.

Anyone find a fix?

---

### Post by hemantparmar on 2010-03-26
thanx... it helped

---

### Post by Fjodr on 2010-05-21
It is most likely a hardware problem. Most manufacturers just send you a new mouse when it happens, implying a rather common problem in the hardware.

However, I would still like to know if it is possible to fix it in ubuntu. There is a Gnome and X setting for the doubleclick speed in milliseconds, and I guess it could be fixed by adding a minimum threshold since the loose contact in the hardware would result in a faster double click than could be expected from a user, effectively putting out a "superhuman" doubleclick.

So, since there is a max. doubleclick speed, shouldn't there be a modifier for min. clickspeed?

---

### Post by jeremyd on 2010-05-29
I have the same problem - but only in relation to the middle button (ie, the scroll wheel), it usually registers as a double click.

It seems the keyboard can be set (under Accessibility, I think it is under Bounce Keys) to ignore fast duplicate keypresses, but I can't see anything similar for the mouse

---

### Post by negora on 2010-12-13
I'm suffering from the same problem on Ubuntu 10.10. My mouse worked flawless until certain day when it started to act at the way which you're describing here. No solution yet. Maybe any update caused this?

PS: It's working fine on another computer which has Lubuntu installed.

---

### Post by lgvh on 2011-02-15
> **negora said:**
> I'm suffering from the same problem on Ubuntu 10.10. My mouse worked flawless until certain day when it started to act at the way which you're describing here. No solution yet. Maybe any update caused this?

PS: It's working fine on another computer which has Lubuntu installed.
Same here, but I have to add something interesting.

I have Machine A and Machine B.

[LIST]
[*]I installed Ubuntu 10.10 i386 in machine A (previous was Ubuntu 10.04), it works perfect (I have used this machine for a while with Ubuntu, I don't use another OS since 3 years ago).
[*]One week ago I need to re-install Ubuntu in machine A, I connected a Genius mouse and a Logitech Trackball, both at the same time. Both look to work ok meanwhile I was doing the installation. (mouse is PS2 and trackball is USB)
[*]When I finish the installation of machine A, I noticed something wrong with the mouse when I do a right-click
[*]I detached the mouse of machine A and put the mouse in machine B to install Ubuntu 10.10 i386 in machine B
[*]Machine B is working correct with the mouse
[*]Machine A is making problems with double clicks frequently
[*]**BUT WHAT IS INTERESTING IS THAT** when I load Ubuntu 10.10 from the CD and run it live, the trackball is doing double clicks to, that it didn't before.
[/LIST]
So I think it is not an update problem, but don't have a clue about what's going on. I am making this comment here to let you know and maybe someone could have an idea. (machine A motherboard is ASUS A8N-VM with the BIOS flashed to the latest available in the manufacturer website)

---

### Post by lgvh on 2011-02-17
I decided to attack the problem from the hardware point of view ...

I add a capacitor of 0.01uF in parallel to each active contact of the micro switch in the mouse and in the trackball (this makes what is called anti-bounce circuit) ... **[SIZE=4]IT WORKS !!![/SIZE]**



Conclusion, the mouse drivers need to have implemented some sort of software anti-bounce algorithm.

---

### Post by isaach on 2011-04-26
> **lgvh said:**
> I decided to attack the problem from the hardware point of view ...

I add a capacitor of 0.01uF in parallel to each active contact of the micro switch in the mouse and in the trackball (this makes what is called anti-bounce circuit) ... **[SIZE=4]IT WORKS !!![/SIZE]**



Conclusion, the mouse drivers need to have implemented some sort of software anti-bounce algorithm.

That's interesting, since the consensus from the discussion on the bug tracker item is that it doesn't seem to be a hardware problem:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/365300](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/365300)

It would seem from what you say and previous posts that it's a common hardware problem that Windows has a software mechanism to correct but Ubuntu/Gnome does not.

---

### Post by Bladeforger on 2011-08-19
> **lgvh said:**
> I decided to attack the problem from the hardware point of view ...

I add a capacitor of 0.01uF in parallel to each active contact of the micro switch in the mouse and in the trackball (this makes what is called anti-bounce circuit) ... **[SIZE=4]IT WORKS !!![/SIZE]**



Conclusion, the mouse drivers need to have implemented some sort of software anti-bounce algorithm.
I'm having the same problem and would be happy to add a couple of capacitors... these go inside the mouse?

---

### Post by rlgracia on 2013-03-01
I started having the same problem a few days ago.  After some searching I found this thread.  I thought maybe it is hardware.  I switched to another mouse and the problem went away.  My guess is it's a bad mouse.

---

