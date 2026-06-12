---
title: "Menu Bar Transparency with Gnome Classic"
date: 2012-05-24
forum: General Help
---

### Post by Jforsyth on 2012-05-24
I'm trying to customize my Gnome Classic theme in Ubuntu 12.04. I'd like to add transparency to the menu bar of each window, if possible. 

I've been able to get everything else I've wanted to be transparent: the gnome panel, drop down menus, Metacity window borders, and right-click menus. I used the Opacity, Brightness, and Saturation plugin in Compiz, as well editing the opacity-related gconf settings in /apps/gwd to do this. I could make the entire window transparent with Compiz, but I haven't figured out a way to target just the menu bar.  

I have some experience modifying GTK+3 CSS files. Is there any way to configure opacity by editing these files for a particular theme?

I've attached picture that highlights what I mean when I say menu bar.

---

### Post by glennric on 2012-05-24
Were you able to get full transparency of the gnome-panel?  By that I mean the applets and everything, and not just transparency of the empty area.  If so how?

---

### Post by Jforsyth on 2012-05-24
> **glennric said:**
> Were you able to get full transparency of the gnome-panel?  By that I mean the applets and everything, and not just transparency of the empty area.  If so how?

I basically followed the instructions [here](http://www.webupd8.org/2009/12/true-transparency-for-gnome-panel.html). Except I didn't disable transparency for PopupMenus and DropdownMenus, because I wanted to keep those. 

Now, I'm not sure if this is guaranteed to make everything transparent for all themes. There's often incompatibilities between the applet style and the panel style. If you do a Google search for "ubuntu full transparent panel" you'll find a lot of tutorials that have you modifying theme settings, so I think it depends on the particular theme you're using and what it specifies for the panel applet behavior. I'm basing my custom theme off of Zukitwo-Dark and it worked with just the Compiz tweak.

---

