---
title: "Nautilus Config"
date: 2010-01-11
forum: General Help
---

### Post by joeknoodle on 2010-01-11
Is there a way to configure the "nautilus file operations window" to pop up at the bottom of the screen, rather than right in the middle where I'm trying to work?

It's getting old having to drag it out of the way all the time.

---

### Post by lyall on 2010-01-11
> **joeknoodle said:**
> Is there a way to configure the "nautilus file operations window" to pop up at the bottom of the screen, rather than right in the middle where I'm trying to work?

It's getting old having to drag it out of the way all the time.

Yes you can

first - open it
second - size it and move it to the location you want
third - close it by using the File > Close

you will have to play with it to your likings 

the next time you open it it should open at the location you closed it at.

if you make it larger and close it, it will open at that size and location
so if you move it around and close it.  It will open there and at that size

I hope this helps

good luck and have fun learning

---

### Post by joeknoodle on 2010-01-12
> **lyall said:**
> Yes you can

first - open it
second - size it and move it to the location you want
third - close it by using the File > Close

you will have to play with it to your likings 

the next time you open it it should open at the location you closed it at.

if you make it larger and close it, it will open at that size and location
so if you move it around and close it.  It will open there and at that size

I hope this helps

good luck and have fun learning
Thanks, but more info is in order...

What's happening is say I copy a file from A to B. During this process a window comes up, titled as above, while the work progresses. I can't resize or reshape the window, but I can (and have to) move it to the bottom. If I close the window, the copy doesn't take, so I have to let the window do its work, and of course then it closes on its own, to return back in the middle of everything upon its next instance.

---

### Post by joeknoodle on 2010-01-18
bump

maybe a setting in one of the QT file thingies?

---

### Post by stinkeye on 2010-01-18
If your using compiz you can create a setting in place windows.
and/or
Set it to below in window rules.
If your not using compiz you could use wmctrl to send it desk 1 with a
one click panel launcher or a shortcut key.
It's a handy launcher anyway, because it will send any acvtive window to desk 1.
Doesn't work with compiz though becuase of the way it draws the desktops.
```
wmctrl -r :ACTIVE: -t 1
```

---

### Post by joeknoodle on 2010-01-18
> **stinkeye said:**
> If your using compiz you can create a setting in place windows.
and/or
Set it to below in window rules.
If your not using compiz you could use wmctrl to send it desk 1 with a
one click panel launcher or a shortcut key.
It's a handy launcher anyway, because it will send any acvtive window to desk 1.
Doesn't work with compiz though becuase of the way it draws the desktops.
```
wmctrl -r :ACTIVE: -t 1
```
Compiz is a no go, but I think that other trick might suffice. It is a shame there's no way to easily configure this. Placing something in the middle of the workspace forces folks to have to move it out of the way to get work done. It's just stupid.

Thanks for the info.

---

### Post by joeknoodle on 2010-01-18
I just noticed, it's not applications per se, but the notification that nautilus is performing an action.

How can I move the notifications window down out of the way?

---

