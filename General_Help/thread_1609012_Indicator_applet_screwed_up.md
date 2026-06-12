---
title: "Indicator applet screwed up"
date: 2010-10-29
forum: General Help
---

### Post by BobvanderPoel on 2010-10-29
I thought I'd install unity to see what it looked like. Opps!!!

It really didn't seem to do anything ... and I think I uninstalled it. But, I now have at least 2 problems:

1. I have a number of menu entries <File> <Edit> which appear to be from Rhythmbox in my indicator-applet in the panel.

2. I seem to be missing the menu completely in gconf-editor. The app does seem to work ... but no menu.

I have reinstalled all the indicator-applet stuff I could find in synaptic, but no difference. I also reinstalled my .config directory from backup. 

Help .. I feel so dumb for even trying this!

---

### Post by gufide on 2010-10-29
me I just see my wallpaper and menu and toolbar appear one frame and oops! just my wallpaper again -_-"

---

### Post by BobvanderPoel on 2010-10-29
Okay ... did it the hard way and I think it's solved.

First I grabbed a nice tool which prints out recent apt changes from:

[http://mavior.eu/apt-log/](http://mavior.eu/apt-log/)

Next, ran that an found out what I'd installed ... cool.

Next, held my breath and did a 

   sudo apt-get remove <list>

where list was to stuff I'd installed earlier.

Good, seems to have worked. I have my proper indicator applet and gconf-editor works. So, I'm marking this thread <solved>.

---

