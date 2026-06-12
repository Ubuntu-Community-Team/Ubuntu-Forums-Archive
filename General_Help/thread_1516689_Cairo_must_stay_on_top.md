---
title: "Cairo must stay on top"
date: 2010-06-24
forum: General Help
---

### Post by jesuisbenjamin on 2010-06-24
Hello there friends,

I just move to 10.04
On installing Cairo i decided to make its icon-size of 20x20, positioned on top, with visibility "always on top". This causes icons to stand in the empty space of the top panel: great.

However: when i click on the panel (gnome menu, system tray, volume, etc.) then the panel moves on top and the dock below. Since icons are 20x20, they do not exceed the size of the panel and i cannot get them back on top.

What happened? How can i get them to stay on top please?

Thanks.
B.

---

### Post by fabounet on 2010-06-24
why do you place the dock at the same place as the gnome-panel ?

you can probably remove completely the gnome-panel and just keep Cairo-Dock, with 1 or 2 docks.

---

### Post by jesuisbenjamin on 2010-06-24
Thanks Fab,

That's because i'd like it to look this way (cf. screenshot), and stay this way.
Cairo offers a neater way of managing launchers than by adding the icons on the panel itself.
If i remove the panel, then i have no menu, no system-tray etc. and i really dislike having them on a dock.

This said, if you know a way to help my dream come true, please tell :)

Thanks

---

### Post by fabounet on 2010-06-25
I know a possible way :)
install the latest version (2.2-beta1), there is a panel view in it.
You can have the equivalent of a gnome-panel, but with the smooth effects of GLX-Dock.
Try for instance the theme called "Unity".

[http://www.glx-dock.org/ww_page.php?p=ppa%20Weekly&lang=en]("http://www.glx-dock.org/ww_page.php?p=ppa%20Weekly&lang=en")

---

### Post by jesuisbenjamin on 2010-06-25
Ok i am going to try that thanks.

Also i have made a partial work-around which i want to share (cf. screenshot).
I created 2 panels, one left another on the right, without expansion. In the gap between i put the dock. I created a background with a sample of the panel, so it looks the same. 

Now if i could expand the background to fill the screen horizontally, then it would create the illusion of a panel-integrated dock.

This said i'll try the beta.

Thanks!

---

### Post by jesuisbenjamin on 2010-06-25
Hi Fab,

I tried the Unity theme but nothing changes.

I also tried my own theme with the panel view, but all it does really is move it to the left of the screen and remove all effects.

Isn't the idea of allowing the background to expand horizontally more sensible?

Thanks

---

### Post by jesuisbenjamin on 2010-06-26
Hi there,

I am adding another screenshot to emphasise the dynamic which Cairo-on-top-of-panel would have.
The interest is to bring the unused space in the middle of the panel to a use. It could be done by adding launcher applets but what Cairo offers is the dynamic and effects which can increase efficiency (not only looks).
With a zoom effect on hovering it is easy to select while at rest, launchers use a minimum space.

If this could be made easy to maintain on top, it would be a great feature, even better would be to implement it as an applet OF Gnome-Panel.

---

### Post by fabounet on 2010-06-26
what I meant is that using the "panel" view, you have something similar to a gnome-panel, allowing you to remove the gnome-panel.

but anyway, if you really want to put the dock and the panel at the same place, try with
cairo-dock --keep-above
(with the latest 2.2 version)

---

### Post by jesuisbenjamin on 2010-06-26
> **fabounet said:**
> 
but anyway, if you really want to put the dock and the panel at the same place, try with
cairo-dock --keep-above
(with the latest 2.2 version)

Yeah! :popcorn:
Why didn't you say so earlier? :D

Thanks! This is so what i wanted. :handshake:

---

### Post by jesuisbenjamin on 2010-06-26
I cried victory too soon.

I added the command: ```
cairo-dock -o --keep-above
```
in Startup Applications.
However the command is not maintained as such and on reboot Cairo is started up ideed, however the command in Startup Applications shows ```
cairo-dock -o
``` only.

How can i make Startup Applications keep the full command-line?

Except for that, it rocks!

Thanks.

---

### Post by jesuisbenjamin on 2010-06-27
The problem solved itself!

---

