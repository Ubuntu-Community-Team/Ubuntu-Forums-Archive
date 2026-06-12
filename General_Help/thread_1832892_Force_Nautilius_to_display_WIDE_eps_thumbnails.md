---
title: "Force Nautilius to display WIDE eps thumbnails"
date: 2011-08-25
forum: General Help
---

### Post by brucewestfall on 2011-08-25
I had a problem of nautilus not displaying thumbnails of .eps and .ps files that were much wider than tall.  Only the generic icon would display.

Here is what I finally found:
open gconf-editor

search for "eps"

/desktop/gnome/thumbnailers/image@x-gzeps
/desktop/gnome/thumbnailers/image@x-bzeps
/desktop/gnome/thumbnailers/image@x-eps

all of these appear.

click each on and change the following line found at the top of the screen:
command evince-thumbnailer -s %s %u %o

change it to:
command evince-thumbnailer -s 800 %u %o

close gconf and go to
/home/<yourhome>/.thumbnails/fail/gnome-thumbnail-factory

delete all the files found there.

Migrate back to whatever folder you were having trouble with and watch the icons appear!  If it doesn't work, do a refresh with CTRL+R

If it doesn't work, experiment and tell everyone what you found!

---

