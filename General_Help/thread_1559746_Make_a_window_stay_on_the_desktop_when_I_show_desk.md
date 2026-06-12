---
title: "Make a window *stay* on the desktop when I show desktop"
date: 2010-08-23
forum: General Help
---

### Post by Zorgoth on 2010-08-23
I use a terminator (a cool terminal emulator) as part of my desktop background.  Using compiz and ccsm, I have cleared up almost all of the problems (it is easy because you can give a terminator a custom window role and title), but I am left with one: when I show desktop, my terminator disappears.  If it is not controlled by compiz's Show Desktop plugin, it minimizes, despite being set in Compiz's window rules to unminimizable.

So I guess show desktop goes deeper than ccsm can control.  So how can I specify windows to keep on the desktop when I show desktop?  It must be possible because cairo-dock and gnome-panel do it, so how can I make my background terminal do it?

---

### Post by Zorgoth on 2010-08-23
solved here:

[http://ubuntuforums.org/archive/index.php/t-1216845.html](http://ubuntuforums.org/archive/index.php/t-1216845.html)

The gconf-editor solution did it for me

---

### Post by stinkeye on 2010-08-24
Just some info for you.
To do this in ccsm go to 
window management > window rules > skip taskbar
and add terminator.

Then go to 
ccsm > general options
and untick **Hide Skip Taskbar Windows**.

Making a window unminimizable just removes the minimize button.

Also if you want other instances of terminator to be minimized when you
show the desktop have a look at this thread using terminal profiles.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=1536252[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1536252")
The same method should work with terminator.

---

### Post by Zorgoth on 2010-08-24
> **stinkeye said:**
> Just some info for you.
To do this in ccsm go to 
window management > window rules > skip taskbar
and add terminator.

Then go to 
ccsm > general options
and untick **Hide Skip Taskbar Windows**.

Making a window unminimizable just removes the minimize button.

Also if you want other instances of terminator to be minimized when you
show the desktop have a look at this thread using terminal profiles.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=1536252[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1536252")
The same method should work with terminator.

Thanks I have it sorted out.  I use terminator --role=Background already for my background terminator so I can set it based on the window roles and use other terminators with different ccsm settings.  You can also force the title.

---

