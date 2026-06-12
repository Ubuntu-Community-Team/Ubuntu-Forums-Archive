---
title: "Wrong theme on login"
date: 2012-06-07
forum: General Help
---

### Post by scottbomb on 2012-06-07
My appearance settings are bluebird, icons are elementary Xubuntu dark. When I boot up and log in, I'm presented with a totally different theme that includes the Gnome icons (this system does not have gnome installed). 

I have to log out and log back in to get my normal desktop. The above only happens on initial boot up.

Any ideas? I'm not sure which package I should file a bug report against.

---

### Post by scottbomb on 2012-06-11
Apparently no one has any ideas? Last week, I installed plasma-desktop. I couldn't get it to work correctly so I uninstalled it. The problem I'm having seems to have started around the same time. Not sure if they are related but I figured I'd throw that in there just in case.

And speaking with my plasma experiment, every time I log in, kde desktop is still selectable although I removed it. Anyone know who to remove it from the light-dm login?

---

### Post by scottbomb on 2012-06-11
Oddly enough, the problem seems to have resolved itself. Not owing to anything I did (that I know of). To be on the safe side, I also ran ```
sudo dpkg-reconfigure lightdm
``` and the problem has yet to recur.

---

### Post by scottbomb on 2012-06-11
Eh... problem is back for some unknown reason. Any ideas? Against which package should I file a bug report?

---

### Post by Toz on 2012-06-11
Interesting problem. Can you post some before and after screen shots?

Also, would nautilus happen to be installed? Perhaps it is interfering.

The other thing you could try is clearing out your saved sessions cache of anything that maybe left over from the plasma install. From a terminal window:
```
rm -rf ~/.cache/sessions
```

---

### Post by scottbomb on 2012-06-14
Nautilus is not installed. Clearing the cache hasn't helped. Next time it happens, I'll post some pics.

I've also noticed that windows try to snap-to when I move one against the edge of the screen, even though I have that option turned off! I also work with 2 monitors so that can be a real pain when I'm trying to move a window to another screen while the computer is trying to make it take up the whole side or corner of the screen.

I strongly suspect it's the new xfce 4.10. I just don't know which packages control these features.

---

### Post by scottbomb on 2012-06-15
Here are the pics on some boot ups showing the wrong theme. 

[IMG]http://scottbomb.com/image/desktop/IMAG0531.jpg[/IMG]

[IMG]http://scottbomb.com/image/desktop/IMAG0532.jpg[/IMG]

[IMG]http://scottbomb.com/image/desktop/IMAG0533.jpg[/IMG]

[IMG]http://scottbomb.com/image/desktop/IMAG0534.jpg[/IMG]

I have to log out (not reboot) and log back in to get to my normal, customized desktop.

[IMG]http://scottbomb.com/image/desktop/IMAG0535.jpg[/IMG]

[IMG]http://scottbomb.com/image/desktop/IMAG0536.jpg[/IMG]

[IMG]http://scottbomb.com/image/desktop/IMAG0537.jpg[/IMG]

[IMG]http://scottbomb.com/image/desktop/IMAG0538.jpg[/IMG]

---

### Post by scottbomb on 2012-07-03
It hasn't recurred in a week or two so I think it may have been "magically" fixed by an update. Who knows?

For now, I'll mark the thread as solved even though I don't know why or how.

---

