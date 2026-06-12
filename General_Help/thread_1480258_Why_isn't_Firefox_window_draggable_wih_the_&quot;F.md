---
title: "Why isn't Firefox window draggable wih the &quot;File&quot; bar?"
date: 2010-05-11
forum: General Help
---

### Post by warnec on 2010-05-11
I'm using the Default Lucid Ambiance theme. What I noticed, and am quite delighted by this fact, is that windows are draggable not only by their titlebar, but the whole area which is black (which means the "File, Edit, etc." menu is draggable as well)

I noticed this behavior in all apps (ex. Synaptic, Evolution) except Firefox. If I want to drag its window, I have to click directly on the titlebar, which is the top half of the black area. I find it confusing. Why is that so? Any way to change it?

---

### Post by warnec on 2010-05-11
So, You have no idea? Noone besides me experienced/noticed it?

---

### Post by solwic on 2010-05-11
> **warnec said:**
> So, You have no idea? Noone besides me experienced/noticed it?

I just tried it and it doesn't work for me in Firefox, either.  Not sure what's causing it, but you're not the only one having an issue with it.  

For what it's worth, Thunderbird (another Mozilla product) doesn't do it, either.

---

### Post by John Bean on 2010-05-11
I suspect it's because in Firefox the menu bar is also a toolbar, even if you haven't put anything on it. Right-click on it and you'll see what I mean.

---

### Post by hariks0 on 2010-05-11
I don't think that the menu bar and Title bar are very far from each other.:) Press and hold Alt to drag a window by clicking and dragging any part of a window. Anyway you can use Easystrokes to move any windows without any modifier keys like Alt, Super etc. Install it from synaptic and enjoy.

---

### Post by lovinglinux on 2010-05-11
Same discussion [here](http://ubuntuforums.org/showthread.php?t=1479858).

> **hariks0 said:**
> I don't think that the menu bar and Title bar are very far from each other.:) Press and hold Alt to drag a window by clicking and dragging any part of a window.

In fact, they are. Although Firefox uses GTK, the tool bars are XUL based, so I don't think they can interact the way other applications menu bars do. When you use ALT, the window manager probably "freeze" everything inside the window decoration and disregard the functions of inner interface, so it can move them altogether.

---

### Post by x-shaney-x on 2010-05-11
It's not so much the distance, it's the fact I get used to moving other windows by grabbing them anywhere in the unified title/menubar.

Firefox is the ONLY non-gtk app I am using so I automatically just grab it anywhere in the area then have to re-adjust, wasting precious seconds.

---

### Post by hariks0 on 2010-05-12
What about Easystroke anyway?

---

