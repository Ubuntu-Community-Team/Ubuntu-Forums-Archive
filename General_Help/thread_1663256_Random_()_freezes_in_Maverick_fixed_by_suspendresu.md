---
title: "Random (?) freezes in Maverick fixed by suspend/resume"
date: 2011-01-09
forum: General Help
---

### Post by goanga on 2011-01-09
Using Maverick with all updates on a Lenovo IdeaPad G560 laptop.
I have a **nVidia Corporation GT218 [GeForce 310M]** graphic card and I'm using the latest driver from the x-swat ppa.
I experience seemingly random freezes, where the system keeps working and the screen gets updated (movies, audio and flash keep playing, notifications popup), but mouse cursor is frozen and keyboard is unresponsive (including Alt-SysRq-*).
However, a suspend/resume cycle (by closing and reopening the lid) fixes it 90% of times (the other 10%, the laptop doesn't resume).
Not using Compiz seems to make the interval between freezes longer, but does not prevent them.
The only observation I can make is that it never (pretty sure) happens while I'm at work and using a mouse, but it happens quite often while I'm at home and using the touchpad.

Any idea?

---

### Post by goanga on 2011-01-10
bump?

At least some ideas about where to look (logs, etc.) for an explanation would be useful!

---

### Post by danieleds on 2011-01-10
what happens if, while it's frozen, you connect an usb mouse?

---

### Post by goanga on 2011-01-12
Plugging in an USB mouse or keyboard works.

I have now narrowed it down to the touchpad failing (there are errors in my /var/log/messages that go **psmouse.c: lost connection with the mouse; trying to reconnect; reconnect failed**), which somehow affects the keyboard as well.

Going on some suggestions from google, I created this file:

```
/etc/modprobe.d/psmouse.conf (or whatever.conf)
```

with the following content:

```
options psmouse proto=imps
```

No more freezes for a day and a half, but the touchpad is less responsive and setting the speed and sensitivity doesn't appear to work.

I also added nohz=off to the kernel options, but I don't think that had anything to do with it.

I'll test some more and if I'm convinced that this was the solution, I'll mark the thread solved.

---

### Post by arsham on 2011-02-17
I'm having the same problem.. 
Did you get to fix it yet? 

EDIT: It just happens while my laptop is on battery

> **goanga said:**
> Plugging in an USB mouse or keyboard works.

I have now narrowed it down to the touchpad failing (there are errors in my /var/log/messages that go **psmouse.c: lost connection with the mouse; trying to reconnect; reconnect failed**), which somehow affects the keyboard as well.

Going on some suggestions from google, I created this file:

```
/etc/modprobe.d/psmouse.conf (or whatever.conf)
```

with the following content:

```
options psmouse proto=imps
```

No more freezes for a day and a half, but the touchpad is less responsive and setting the speed and sensitivity doesn't appear to work.

I also added nohz=off to the kernel options, but I don't think that had anything to do with it.

I'll test some more and if I'm convinced that this was the solution, I'll mark the thread solved.

---

### Post by arsham on 2011-02-18
Found this fix : 
downgraded pm-utils to this version :  1.3.0-1ubuntu1
No freeze anymore..
cheers

---

