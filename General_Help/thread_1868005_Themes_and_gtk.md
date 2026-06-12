---
title: "Themes and gtk"
date: 2011-10-23
forum: General Help
---

### Post by ked on 2011-10-23
I recently upgraded to 11.1 and have ran into a couple of customization issues.

I'm trying to tune my environment and I'm quite satisfied with colors and fonts, but I'm a bit confused when it comes to scrollbars, and in particular the gnome-terminal one. I find the "GNOME color chooser" very convenient, but it seem to onlyn alter gtk-2 related stuff. It seem that the gnome-term window consist of both gtk-2 and gtk-3 elements, but I can't figure out what files to edit for changing the probably gtk-3 related scrollbar in "gnome-terminal".
Anyone out there interested in this scrollbar issue? I really like to change it's contrast and/or color.

---

### Post by linuxinstalledfromhdd on 2011-10-23
> **ked said:**
> I recently upgraded to 11.1 and have ran into a couple of customization issues.

I'm trying to tune my environment and I'm quite satisfied with colors and fonts, but I'm a bit confused when it comes to scrollbars, and in particular the gnome-terminal one. I find the "GNOME color chooser" very convenient, but it seem to onlyn alter gtk-2 related stuff. It seem that the gnome-term window consist of both gtk-2 and gtk-3 elements, but I can't figure out what files to edit for changing the probably gtk-3 related scrollbar in "gnome-terminal".
Anyone out there interested in this scrollbar issue? I really like to change it's contrast and/or color.

Me too. I've tried several differerent how-tos online to make the changes I want, but none of them are working.  I miss the old way we could change Appearance in 10.10. We only have like 4 themes to choose from now.  And you can't really do much with them.

---

### Post by Frogs Hair on 2011-10-23
There is a section at the link that addresses disabling the overlay scroll bars . [http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

---

### Post by ked on 2011-10-24
> **Frogs Hair said:**
> There is a section at the link that addresses disabling the overlay scroll bars . [http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

Sorry, I forgot to say I've already disabled the overlay scrollbar. I just want to change the color of the old fashion one.

---

### Post by vasa1 on 2011-10-24
> **ked said:**
> ...
Anyone out there interested in this scrollbar issue? I really like to change it's contrast and/or color.

Yes! I don't know why it's not being seen as an **accessibility** issue. Instead, it's being treated as a "tweaking" or "customization" issue and being given less importance.

There are two bugs but ...
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/563474](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/563474)
with this: "Or set colorize_scrollbar to TRUE in theme gtkrc file. But it will work till next theme update :)" which I haven't tried
and
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/537048](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/537048)

---

### Post by vasa1 on 2011-10-24
Change colorize from FALSE to TRUE in gtkrc (for gtk-2.0 stuff).

Works for me. Now I get decent contrast in LibreOffice.

---

### Post by ked on 2011-10-24
> **vasa1 said:**
> Change colorize from FALSE to TRUE in gtkrc (for gtk-2.0 stuff).

Works for me. Now I get decent contrast in LibreOffice.

Yes, it works for gtk-2.0 stuff, but some apps seem to be dependent on both gtk-2.0 and gtk-3.0 stuff. I can't change the Evolution mail or Gnome terminal scrollbar color, but works nice for most other apps. Really annoying...

---

### Post by ked on 2011-10-24
I can see that the almost invisible scrollbars in the Ambiance theme has been an issue before, and that the problem was solved for gtk-2.0 stuff. But I understand that gtk-3.0 stuff is not affected by these solutions. I've been trying to figure out how colors are set in the Ambiance gtk-3.0 files, but I can't figure it out, and really I don't have time for this. (It's not within the scope of my project... :P)
There are some color definitions I haven't edited in the different gtk.css files around. Maybe I'll play around a bit there to see what happens.

Cheers...

---

### Post by ked on 2011-10-24
Finally!!! I found a way to change the gtk-3.0 scrollbar within the Ambiance theme to get both stepper buttons and a good contrast of the scrollbar.


~$sudo gedit /usr/share/themes/Ambiance/gtk-3.0/gtk-widgets.css

scroll (if you can see the scrollbar...) to the 

/*************
 * scrollbar *
 *************/

section (line 1252), and set

    -GtkScrollbar-has-backward-stepper: 1;
    -GtkScrollbar-has-forward-stepper: 1;

if you like the stepper buttons activated.

Then, in the ".scrollbar.trough.vertical" section (just under), change the "bg_color" to for instance #A5A5A5 (or any color you like) so the section looks like this:

    background-image: -gtk-gradient (linear, left top, right top,
                                     from (shade (#A5A5A5, 0.9)),
                                     to (shade (#A5A5A5, 0.95)));

As far as I see, this helps for gtk-3.0 apps only (like Evolution and gnome-terminal).

Hope this can be useful for others, or did I just invent the wheel again?

:D

Cheers...

---

### Post by ked on 2011-10-24
> **LIONFURY said:**
> Change colorize from FALSE to TRUE in gtkrc (for gtk-2.0 stuff).

Works for me. Now I get decent contrast in LibreOffice.

I did that for better scrollbars for the gtk-2.0 stuff, but it didn't do anything for the gtk-3.0 stuff, but now it works nice.

---

### Post by vasa1 on 2011-10-25
> **ked said:**
> Finally!!! I found a way to change the gtk-3.0 scrollbar within the Ambiance theme to get both stepper buttons and a good contrast of the scrollbar.


~$sudo gedit /usr/share/themes/Ambiance/gtk-3.0/gtk-widgets.css
...
Hope this can be useful for others, or did I just invent the wheel again?

:D

Cheers...

Thanks for hunting down the specific file!

I modified lines #1292 and 1293 to #800000. That's all.

---

### Post by vasa1 on 2011-12-06
> **vasa1 said:**
> Change colorize from FALSE to TRUE in gtkrc (for gtk-2.0 stuff).

Works for me. Now I get decent contrast in LibreOffice.

Even better is to use gnome color chooser for gtk-2.0 stuff. But I had to revert TRUE to FALSE in order the make the choice of my color for the scrollbar thumb to work.

---

### Post by Spyderkid on 2011-12-06
I know the tread is solved, but I've just written a how to on customizing ubuntu 11.10 themes, icons themes, and cursors

Change your icon theme and GTK theme: [http://ubuntuforums.org/showthread.php?t=1890460](http://ubuntuforums.org/showthread.php?t=1890460)

Change your cursor:
[http://ubuntuforums.org/showthread.php?t=1891402](http://ubuntuforums.org/showthread.php?t=1891402)

---

