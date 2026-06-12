---
title: "How to configure PS/2 scroll wheel mouse"
date: 2010-07-07
forum: General Help
---

### Post by jay214128 on 2010-07-07
When I originally installed 10.04 on a new machine, I was using a temporary PS/2 keyboard and PS/2 mouse.  The mouse was a simple two-button mouse.  This worked fine.  Now, I have moved my Microsoft PS/2 scroll wheel mouse from my previous computer to the new machine, but the scroll wheel does not work.  How do I make it work?

I had hoped that Ubuntu would detect my different (new) hardware and configure it for me, but it did not.  Googling leads me to xinput, but I can't figure out what to do with that and it indicates it is for 'on the fly' configuration.  I want it to be permanently configured.  Is there some way to invoke the installation tool again to reinstall the mouse?

---

### Post by jay214128 on 2010-07-19
Update - sometimes when I boot, the scroll wheel works.  Most of the time it does not.  It appears that Ubuntu is dynamically configuring this on every boot, but doesn't get it right most of the time.  Is there some way to statically configure this?

---

### Post by WorMzy on 2010-07-19
You can declare static hardware configurations in /etc/X11/xorg.conf

[http://ftp.x.org/pub/X11R7.0/doc/html/mouse.4.html](http://ftp.x.org/pub/X11R7.0/doc/html/mouse.4.html)

---

### Post by jay214128 on 2010-07-24
I looked at the xorg.conf configuration information, but I don't know how to make that work for me.  There is no /dev/mouse on my system.  Further googling has led me to believe that Ubuntu no longer uses xorg to configure the input devices (mouse), but instead uses udev.  A search for all things "mouse" in my /dev yields:

```
/dev/.udev/links/input\x2fby-path\x2fplatform-i8042-serio-1-event-mouse
/dev/.udev/links/input\x2fby-path\x2fplatform-i8042-serio-1-mouse
/dev/.udev/db/input:mouse1
/dev/.udev/db/input:mouse0
/dev/input/mouse1
/dev/input/by-path/platform-i8042-serio-1-event-mouse
/dev/input/by-path/platform-i8042-serio-1-mouse
/dev/input/mouse0
```

I looked at some of the rules in /dev/udev/rules.d, but am way over my head.  It looks like a bug in the kernel mouse detection code that sometimes detects the mouse correctly, and mostly does not.  Should I file a bug?  How/where would I do that?

Jay

---

### Post by jay214128 on 2010-07-29
Looks like this may be a known bug ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/587134](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/587134)).

---

### Post by jay214128 on 2010-08-07
For those who might find this thread with the same or similar problem, I resolved it by buying a new USB mouse.  I'm now using a Logitech Performance Mouse MX and it works correctly by just plugging it in :-)

---

