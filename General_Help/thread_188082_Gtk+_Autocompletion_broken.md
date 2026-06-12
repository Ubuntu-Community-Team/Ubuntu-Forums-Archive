---
title: "Gtk+ Autocompletion broken"
date: 2006-06-03
forum: General Help
---

### Post by psychicdragon on 2006-06-03
There's something up with the autocompletion of paths in the Gtk+ filechooser. It seems to be horribly broken from my perspective. I haven't filed a bug yet, just wanted to see if anyone else is experiencing this.

Here's the basic series of events:

[LIST=1]
[*]Open up a Gtk+ open file chooser.
[*]Hit ctrl+l to get the location entry.
[*]Start typing a path (I was trying to get to /usr/share/icons/).
[*]It will complete it for you (I had typed /usr/share/ic, it completed it to /usr/share/icons/).
[*]Hit enter.
[*]Error pops up, stating that /usr/share/ic does not exist.
[/LIST]

---

### Post by bjc on 2006-06-03
Strange. I can't reproduce that on Gnome.

---

### Post by psychicdragon on 2006-06-03
[QUOTE=bjc]Strange. I can't reproduce that on Gnome.[/QUOTE]
Thanks for the reply. Maybe it's because I'm using Xubuntu...?

I'll bump this thread, see if anyone else is noticing this issue. :KS

---

