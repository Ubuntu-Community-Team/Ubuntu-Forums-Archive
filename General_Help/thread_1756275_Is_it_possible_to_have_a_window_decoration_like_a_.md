---
title: "Is it possible to have a window decoration like a clock? What else?"
date: 2011-05-12
forum: General Help
---

### Post by aaronchall on 2011-05-12
I have my toolbars (top and bottom) set to autohide to save screen real estate, but I need to have a clock so I always know what time it is (my clock widget keeps disappearing). There's actually tons of real estate going to waste on the top window bar. I know the program I'm looking at, and I know where I am. I think it would be cool if we could just get rid of the top bar thing, or at least make it 1/3 the size. 

Otherwise, I'd like to have a clock on it, at least, since it's completely blank all the way across to the right side of the screen.

Aaron

---

### Post by Matt__ on 2011-05-12
Screenlets will give you any number of desktop widgets, including several clocks and system monitors. you can even set different screenlets for each workspace.

On my main system I have removed BOTH panels and just use a cairo dock (docky  or avant window navigator (AWN) would work too) that auto hides at the bottom...so like a mac but nicer. The dock has all my main apps and the main menu button for things i use less. It also has network/time/home/docs/pics/music/movie icons and off course the trash can and terminal.

to remove the panels do
```
sudo chmod -x /usr/bin/gnome-panel
```
which will stop the panel from loading at boot (or rather it stops it being executable), and if you ever need it back just;
```
sudo chmod +x /usr/bin/gnome-panel
```

log out for it to take effect.

---

### Post by aaronchall on 2011-05-12
Matt, I would really prefer not to use the screenlet, and I like my otherwise hidden toolbar panels.

Some people like sparse/clean. I am a multitasker. I have a lot of things going. I have a computer with the capabilities for multitasking, so I have a lot of things I'm working on open at a time. I like my panels. 

What I'm looking for is the ability to have a clock sit at the top right of any open window. 

The screenlet is workable. 

I thought I had a good workable solution with the top panel, by turning off expand and undoing autohide, I could have the panel in the center of the window bar at the top. But turning off autohide makes maximized windows sit below the panel, reducing the workspace again. Is there a way to make the maximized window sit at the very top of the screen?

Right now I'm using a digital widget, top front and center, I suppose this is close to ideal, but how do I make sure it comes up every time I reboot?

Aaron

---

