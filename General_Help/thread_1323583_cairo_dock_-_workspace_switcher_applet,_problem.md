---
title: "cairo dock - workspace switcher applet, problem"
date: 2009-11-11
forum: General Help
---

### Post by LifeEnemy on 2009-11-11
I've been trying to set up Cairo dock to hold shortcuts, widgets, launchers and things like that. Basically, everything except the active windows (I find I prefer the stand panels, go figure). Anyway, I've had trouble before with the workspace switcher totally breaking and not working no matter what. I had to totally uninstall/reinstall cairo dock and delete the config files to make it work (multiple times). I just recently figured out that the problem is caused, for some reason, whenever the option to "Show currently open applications in the dock" is *not* checked. I don't know why this would be happening, but it is and it's easy reproducable. I don't want to just hide the bar somehow because it takes up resources and causes the minimize animation to move toward the dock rather than the gnome panel I use. Can anyone help?

---

### Post by fabounet on 2009-11-12
the fact is that currently the switcher needs the taskbar module (to display windows on its icon, to keep track of the current desktop, to display the list of windows in a menu on middle-click, etc).

so you'll have to activate the taskbar to use this applet corerctly.
But you can use the option "show minimized window only", which will make a very light taskbar (the same as MacOSX).

---

### Post by LifeEnemy on 2009-11-12
Well that sucks. I guess I'll either have to come up with a way to sufficiently hide the list of windows, or just put the desktop switcher back on my gnome panel.

---

### Post by fabounet on 2009-11-13
I've fixed it yesterday, so it's now available on the bzr branche :-)
if you don't want to compil it from the sources, the weekly packages will be available in a few days on Launchpad.

---

### Post by LifeEnemy on 2009-11-13
That's great! Thanks for the fix. I don't know enough about linux to compile from source, so I'll wait for the PPA. Can someone post the link to the correct page, just so I know I'm getting the right one? I haven't done much like this before. I'm running Jaunty if that matters.

---

### Post by fabounet on 2009-11-16
here is the page that explains how to install the PPA (it's very easy, just like a normal reposiroty.)
[https://launchpad.net/~cairo-dock-team/+archive/weekly]("https://launchpad.net/~cairo-dock-team/+archive/weekly")

It's updated around once a week.

---

### Post by LifeEnemy on 2009-12-22
The update worked perfectly. The applet switches desktops just like it should. However, I just noticed one thing: while switching desktops works great, the function when using middle click (shows a list of all windows open on all desktops), only works when the dock is tracking currently open windows. When the option is unchecked, the middle-click window appears but doesn't list any open windows.

I'm not trying to sound ungrateful. The update is great, thanks for the hard work. It fixed a major problem (for me), and this one is relatively minor, but I thought that I should bring it to light so it can be fixed at some point.

---

### Post by fabounet on 2009-12-23
yes the switcher only displays the list of known windows.
so it can do its job perfectly without the taskbar (means it can switch to another desktop, display the current one, etc), but it can only display the currently know windows (either in the middle click menu or on the icon)
this is a limitation of the system at the moment. ^_^

---

