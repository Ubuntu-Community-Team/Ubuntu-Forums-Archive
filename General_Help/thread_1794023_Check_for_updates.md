---
title: "Check for updates"
date: 2011-06-30
forum: General Help
---

### Post by Monotoko on 2011-06-30
Hi All,

If I do ctrl+alt+f1 and login it tells me when there are updates available. I would like it to do the same if I open a terminal in the GUI, how would I go about configuring that?

Daniel

---

### Post by polki@mac.com on 2011-07-01
I would like to know this as well.

---

### Post by mendhak on 2011-07-01
Hi, try changing the shortcut of your terminal to

gnome-terminal -e /path/to/script

where /path/to/script contains

apt-get --no-act upgrade

So that it can check and display a message.  I'm not in front of a terminal right now so you'll need to try this yourself.

---

