---
title: "top panel icons disappear randomly"
date: 2010-06-27
forum: General Help
---

### Post by mich4elp on 2010-06-27
Randomly, when I start up my computer, the top panel will have some icons missing, or an icon will be covered up by part of another.
Example:
[IMG]http://i48.tinypic.com/34et2mq.png[/IMG]

Note that half of the battery icon is shown where the network manager applet should be. Here is what it is supposed to look like:
[IMG]http://i46.tinypic.com/2819641.png[/IMG]

This happens very randomly. As you can see by the times, both of those were taken on the same day. I logged out and logged back in, and it look fine.

---

### Post by krishnandu.sarkar on 2010-06-27
Same Problem [[IMG]http://img517.imageshack.us/img517/797/83015390.th.jpg[/IMG]](http://img517.imageshack.us/i/83015390.jpg/)

---

### Post by hansdown on 2010-06-27
It's being looked at. Bug reports have been made.

Same thing here. It gave me a chance to try cairo dock. Funny thing is, firefox loads super fast from there.

---

### Post by mich4elp on 2010-06-28
Good to know it's not just me then. :)

---

### Post by dvn3ch on 2010-06-28
Similar problem here but the icon for the network just disappeared and the network fails to recognize any wired, wireless, or mobile broadband connection.  I still have the network manager front end but the networking ability just went away...along with the icon.

I have attempted all the possible solutions that I could find on the web but no joy.  So I have had to resort to a new install of 10.04.

Strangely, this is the first real problem that I have had with Linux/Ubuntu.  As luck would have it, this was an install for a friend of mine that I finally convinced to switch over.  He has been fairly cool about it and was amazed at the amount of knowledge that resides on the web about a system that he "hardly knew existed until a few months ago".  I have six systems running Ubuntu (in various releases and editions) and have installed it in about 14 other systems (friends, family, colleagues, etc.).  Honestly, this is the first problem I was stumped on.

Although I have already made a new install, if anyone else wants to take a stab at the problem please feel free to throw out a possible solution.  It may come in handy for me (or someone else) in the future.

---

### Post by saty on 2010-07-02
Check out this thread. 
[http://wwww.ubuntuforums.org/showthread.php?t=1518838](http://wwww.ubuntuforums.org/showthread.php?t=1518838)

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
This code resets the panel to the original defaults.

---

### Post by oxf on 2010-07-02
I'm getting a similar if not absolutely identical problem. See my other thread:
[HTML]http://ubuntuforums.org/showthread.php?t=1515641[/HTML]

The first PC had chunks blacked out from the Wireless icon and now a strange dotted line around it on boot and dotted line around icon in the bottom panel.

I just installed 10.04 on a different machine and get the dotted line thing again. Also the Wireless icon sometimes loads in the panel multiple times or not at all. And a few random strange things with other panel icon too!

---

### Post by imnichol on 2010-07-18
I've noticed this on several different computers using the default theme.  What's the launchpad bug number?  I'd like to subscribe to it.

---

### Post by mjuhasz on 2010-07-18
> **imnichol said:**
> I've noticed this on several different computers using the default theme.  What's the launchpad bug number?  I'd like to subscribe to it.

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/439448](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/439448)

---

### Post by goltoof on 2010-10-13
Any progress on this apparent bug??

Happens to me all the time, just now the sound control icon disappeared, so did the networking icon.  Typically it's the important icons that disappear while the not so important ones always show. Very annoying.

In addition, restarting gnome-panel makes the default tray icons appear again but then all my shortcut icons disappear!!!

What's up Ubuntu?!??

---

### Post by dsfitzpat on 2010-11-15
This problem (while annoying) has a quick fix - at least, until the next time it happens.  Just go into the panel properties, and increase the size by a few pixels.  After you increase it a couple of notches the icons should return to normal, and then you can put the size back to the default and the icons will remain in their correct state.

---

### Post by jrarrmy on 2010-12-13
The pixel thing didn't work for me, but I had to both add them back to the panel myself then reboot and uncheck and recheck **expand** under panel properties to get rid of the blank space that was left behind but I couldn't move any icons there until after that.

---

