---
title: "running a command in the Alt+F2 prompt possible in bash scripts?"
date: 2010-01-05
forum: General Help
---

### Post by bruno9779 on 2010-01-05
Is running a command in the Alt+F2 prompt possible in a bash script?

I need this for a launcher for gnome-shell.
For it I have written a little script to check if the process gnome-shell is alive and act accordingly.
The script works fine, I just don't know how to write "debugexit" to the Alt+F2 prompt, as that is the only decent way I have found to shut gnome-shell down and going back to gdm desktop smoothly.

---

### Post by askreet on 2010-01-05
Redirect your output to /dev/tty2, for example:
echo "My debug output to appear in ALT-F2 terminal!" >/dev/tty2

EDIT:  You will have to be root.

---

