---
title: "Random mouse grabs of dialogs/windows"
date: 2012-04-30
forum: General Help
---

### Post by imbjr on 2012-04-30
I first noticed this with Disk Utility. I go to press the SMART Data button with the window not fully maximised and suddenly I'm in windows grab mode and the cursor is no where near the window it's grabbed (one from behind the window that had focus) - being off to the far left and upwards. Then it happened in Evolution. This happens randomly and is not easily repeated.

I thought this might be be some default XFCE setting, but I've played with them and then I thought it might be the Wacom graphics tablet injecting mouse events, but this has happened on my netbook too.

---

### Post by imbjr on 2012-04-30
> **imbjr said:**
> I first noticed this with Disk Utility. I go to press the SMART Data button with the window not fully maximised and suddenly I'm in windows grab mode and the cursor is no where near the window it's grabbed (one from behind the window that had focus) - being off to the far left and upwards. Then it happened in Evolution. This happens randomly and is not easily repeated.

I thought this might be be some default XFCE setting, but I've played with them and then I thought it might be the Wacom graphics tablet injecting mouse events, but this has happened on my netbook too.

Mmm, one common factor between Disk Utility and Evolution is they are Gnome apps. I'm trying to recall if I've seen this happen with a 3rd app, but nothing comes to mind.

---

### Post by M_Mynaardt on 2012-04-30
> **imbjr said:**
> I first noticed this with Disk Utility. I go to press the SMART Data button with the window not fully maximised and suddenly I'm in windows grab mode and the cursor is no where near the window it's grabbed (one from behind the window that had focus) - being off to the far left and upwards. Then it happened in Evolution. This happens randomly and is not easily repeated.

I thought this might be be some default XFCE setting, but I've played with them and then I thought it might be the Wacom graphics tablet injecting mouse events, but this has happened on my netbook too.

I was having similar problems with AbiWord in particular, which was also not responding to many hot-keys at all.  And similar problems, although not as bad, with gedit.

They were both working just fine under 11.10.

---

### Post by imbjr on 2012-05-01
> **M_Mynaardt said:**
> I was having similar problems with AbiWord in particular, which was also not responding to many hot-keys at all.  And similar problems, although not as bad, with gedit.

They were both working just fine under 11.10.

Agreed. Probably not related, but have you noticed display glitches with xfce4-terminal? I've moved over to xterm for now as xfce4-terminal will start glitching the lower part of the screen where I set up a gnome-2-like panel i.e. running apps shown at the bottom of the screen.

---

### Post by M_Mynaardt on 2012-05-01
> **imbjr said:**
> Agreed. Probably not related, but have you noticed display glitches with xfce4-terminal? I've moved over to xterm for now as xfce4-terminal will start glitching the lower part of the screen where I set up a gnome-2-like panel i.e. running apps shown at the bottom of the screen.

I've not noticed any glitches with my Xfce terminal, no.  So far, the only glitches I've found are the problems with*AbiWord* and *gedit*.  I have not noticed the random grab and move problems with other apps so far.

I also like using *Cairo Dock* on my desktop, and that doesn't seem to have been affected either.  I'm thinking the problems are a bit of a hiccup between Precise Pangolin and a few apps.

It would be more useful if I knew what to look for to fix things up a bit!
:confused:

---

### Post by pbrane on 2012-05-05
If I'm reading this right I have a similar issue. I can run any program and resize the window then click inside the window and the mouse grabs the window above the upper left corner and moves the window around. I upgraded from xubuntu 11.10 to xubuntu 12.04.

Another weird issue is with glade UI designer. The tool palette on the left will "scroll" out of view when I put the mouse cursor over the palette while in icon view.

This may have something to do with upgrading as opposed to re-installing. If I can't figure this out I may try installing fresh. If that fixes the problem I'll post back.

---

### Post by M_Mynaardt on 2012-05-06
> **pbrane said:**
> If I'm reading this right I have a similar issue. I can run any program and resize the window then click inside the window and the mouse grabs the window above the upper left corner and moves the window around. I upgraded from xubuntu 11.10 to xubuntu 12.04.

Another weird issue is with glade UI designer. The tool palette on the left will "scroll" out of view when I put the mouse cursor over the palette while in icon view.

This may have something to do with upgrading as opposed to re-installing. If I can't figure this out I may try installing fresh. If that fixes the problem I'll post back.


That pretty much sounds like the sorts of problems I'm having with AbiWord.  I've not really noticed that with other apps, though.

---

### Post by pbrane on 2012-05-06
A little more research shows this to be a resize grip bug. I can disable the resize grip that shows up in the lower right corner of some applications and it fixes the grab issue. Or avoid using the resize grip altogether.

Here are some links that may help:
[https://bbs.archlinux.org/viewtopic.php?pid=1097116]("https://bbs.archlinux.org/viewtopic.php?pid=1097116")
[http://xubuntu.org/news/window-resizing-in-xubuntu-and-xfce/]("http://xubuntu.org/news/window-resizing-in-xubuntu-and-xfce/") read the part about the resize grip in this one.

Supposedly the bug has been fixed, but not for me. Maybe there are still some regressions that haven't been dealt with yet.

Disabling the resize grip for now seems to help, Edit (or create) **~/.config/gtk-3.0/gtk.css** and add
```

* { 
        -GtkWindow-resize-grip-height: 0;
        -GtkWindow-resize-grip-width: 0;

  }

```

This hasn't fixed the glade ui designer tool palette issue for me though.

---

### Post by imbjr on 2012-05-08
> **pbrane said:**
> A little more research shows this to be a resize grip bug. I can disable the resize grip that shows up in the lower right corner of some applications and it fixes the grab issue. Or avoid using the resize grip altogether.

Here are some links that may help:
[https://bbs.archlinux.org/viewtopic.php?pid=1097116]("https://bbs.archlinux.org/viewtopic.php?pid=1097116")
[http://xubuntu.org/news/window-resizing-in-xubuntu-and-xfce/]("http://xubuntu.org/news/window-resizing-in-xubuntu-and-xfce/") read the part about the resize grip in this one.

Supposedly the bug has been fixed, but not for me. Maybe there are still some regressions that haven't been dealt with yet.

Disabling the resize grip for now seems to help, Edit (or create) **~/.config/gtk-3.0/gtk.css** and add
```

* { 
        -GtkWindow-resize-grip-height: 0;
        -GtkWindow-resize-grip-width: 0;

  }

```

This hasn't fixed the glade ui designer tool palette issue for me though.

Mmm, I just had this happen again (twice) for the first time in just over a week with the Mines game. After pressing the game option "99 mines" suddenly the game darts off lower and to the right with the mouse now in grip mode and dragging the window around.
I'm struggling to see how this relates to the resize-grip problem and the issue is not easily reproducible.

---

### Post by imbjr on 2012-05-08
One thing I've noticed:

Clicking on, and holding on, the title bar of a window sees one go into grab mode, but only after a little delay. You'd think this would be immediate. I wonder if somehow a mouse event is being delayed and whatever window is underneath a dismissed window is receiving that event and treating it as a grab. This however does not explain why the window is so dislocated from the grab point.

---

