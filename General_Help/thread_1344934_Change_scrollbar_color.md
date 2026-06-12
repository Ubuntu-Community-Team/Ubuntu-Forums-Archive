---
title: "Change scrollbar color?"
date: 2009-12-03
forum: General Help
---

### Post by mju4t on 2009-12-03
Hello,

I am running Karmic (and gnome) I changed the appearance of my computer so that my panel is black, as well as all my windows and such.  this has been great, except for one thing - I can't see the scroll bar thingy!  I can see the arrows to scroll but I can't see the actual slider.  Does anybody know of a workaround?

Thanks!
Alex

---

### Post by krunalpatel on 2010-11-19
sudo apt-get install gnome-color-chooser


if you havnt solved this yet....this is the best way to do it

---

### Post by naptastic on 2011-10-17
Add these lines to ~/.gtkrc-2.0:

  style "gnome-color-chooser-scrollbar"
  {
    bg[NORMAL] = "#F07746"
    bg[PRELIGHT] = "#D76A3E"
    bg[ACTIVE] = "#BD5D37"
  }
  widget_class "*Scrollbar" style "gnome-color-chooser-scrollbar"

Change the hex color values to what you like. Prelight is the color while the mouse is hovering over the scrollbar, and active is the color while it's being held down.

---

