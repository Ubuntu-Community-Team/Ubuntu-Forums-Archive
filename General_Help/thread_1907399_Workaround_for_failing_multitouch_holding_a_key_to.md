---
title: "Workaround for failing multitouch: holding a key to scroll?"
date: 2012-01-11
forum: General Help
---

### Post by Dingbats on 2012-01-11
I'm running Ubuntu 11.10 on a laptop that it apparently doesn't support multitouch on.  Thus all my touchpad can do is move the mouse pointer, it can't scroll.  But would it be possible to work around this by making it so whenever I hold the, for example, AltGr key and touch the trackpad, it will scroll instead of moving the pointer?  How would I do this?

---

### Post by Dingbats on 2012-02-01
Bumping this.  Would it work?

---

### Post by xyzzyman on 2012-02-01
Do you know if it's a synaptics touchpad? Mine doesn't support it out of the box, even after I try turning two-finger scroll on via system settings, so I have to manually configure it. At the very least it should still support edge scrolling, because all that does is look at the x coordinate and once it's past a certain point it's in the scroll area.

---

### Post by Dingbats on 2012-02-01
> **xyzzyman said:**
> Do you know if it's a synaptics touchpad? Mine doesn't support it out of the box, even after I try turning two-finger scroll on via system settings, so I have to manually configure it. At the very least it should still support edge scrolling, because all that does is look at the x coordinate and once it's past a certain point it's in the scroll area.
I'm pretty sure it's a synaptics touchpad, yes.

How did you manually configure yours?  Because what I want to do shouldn't be dependent on what kind of touchpad it is, it could even be a mouse.  When I hold eg. the AltGr key, the touchpad/mouse should scroll instead of moving the pointer.  Intuitively, it sounds like a pretty simple operation to me, but I have no idea how to script it.

---

### Post by Dingbats on 2012-02-04
Anyone?  Couldn't be that hard, could it?

if AltGr is pressed:
[INDENT]mouse movement scrolls[/INDENT]
else:
[INDENT]mouse moves pointer[/INDENT]

Basically, I just don't know how to make it happen.

---

### Post by xyzzyman on 2012-02-04
If you want that you will just have to write a program, it's not going to be a simple script. I don't think you'll find someone else to, as they'll just say if you're going to touch the keyboard just press the arrow key.

---

