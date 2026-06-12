---
title: "Mouse click speed too fast, please help"
date: 2009-08-01
forum: General Help
---

### Post by Blackie_Chan on 2009-08-01
Hi all, 

I've been having a mouse click speed problem for a long time now and I need help fixing it. When I single-click something, a double click is action is made. To run applications, I should just single click on items in my panel, and the application will be launched, but with my problem, 2 or more instances of the same application gets launched.

Sometimes when I reboot, I'll be able to get the desired behaviour (single click actions) for up to an hour, then the problem shows up again. 

I have a dual-boot machine and I don't have the problem when I boot to Windows XP (so I don't think it's a hardware problem).

What I've tried:
1. Changing 'Double-click timeout' in Systems > Preferences > Mouse, and then restarting my computer.

2. Adding the lines '*multiClickTime: 1000' in to $HOME/.Xresources, and then restarting my computer. I also tried adding the entry into /etc/X11/Xresources/x11-common. 

At the moment, I've ran out of ideas and considering either going back to Windows or trying another distribution.

Thanks in advance

---

### Post by Post Monkeh on 2009-08-01
dunno how you've set up the mouse, or if it'll do what you want, but on my ubuntu, in my system > preferences menu, the mouse option's accessability menu lets you set up a simulated second mouse click bu holding down the main button.  with some tweaking, surely this could be used to allow a quick click to activate your menu/panel apps, while a slightly longer hold could be used to give you a double click everywhere else?

---

### Post by Blackie_Chan on 2009-08-01
Disregard my last post. It's a hardware problem (I'll have to buy a new mouse). I booted to Windows XP and was logged on for over 5 hours, and found that I had the same problems.

---

### Post by el.maquis on 2011-06-13
It doesn't work for me with SopaUI, Eclipse, ...
Another solution for non-gnome apps: [http://ubuntuforums.org/showthread.php?t=221642](http://ubuntuforums.org/showthread.php?t=221642)

It creates/modifies a file $HOME/.Xresources with the line "*multiClickTime: 400" (where 400 is the timeout in millis)

---

