---
title: "Kubuntu Crashes on startup"
date: 2006-04-15
forum: General Help
---

### Post by jswan on 2006-04-15
Greetings,

I recently installed kde-desktop for kicks and giggles.  Now whenever I turn on computer it tries to load up kde instead of gnome and crashes everytime.  It then lets me backtrace or whatever, blah blah blah.  After it crashes I need to go into the terminal and start up gdm.

The question is how do i get it to default to gdm again instead of kde?

THANKS!

---

### Post by Elif Tymes on 2006-04-15
cd /etc/X11/
then vi default-desktop-manager (or pico, or whatever text editor you prefer)

Then change it from '/usr/bin/kdm/' to '/usr/bin/gdm'

That should work :)

---

### Post by jswan on 2006-04-15
thanks elif,  worked great

it was actually /usr/sbin/gdm though

---

### Post by Elif Tymes on 2006-04-15
Oh, my install must be slightly different :) Glad it works now though.

---

