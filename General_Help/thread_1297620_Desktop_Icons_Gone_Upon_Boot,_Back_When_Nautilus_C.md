---
title: "Desktop Icons Gone Upon Boot, Back When Nautilus Called"
date: 2009-10-21
forum: General Help
---

### Post by Gias Kay on 2009-10-21
Hello all,

I posted this problem in Main Support Categories > Desktop Environments but didn't receive many responses so I thought I'd try posting at here again.

This problem has been haunting me since I upgraded from Intrepid to Jaunty. I figure it's time to find a solution for it before I advance into Karmic.

At first (immediately after the upgrade), I lost my Metacity shortcut to open up a new nautilus window. Then someone instructed me to use CompizConfig Settings Manager and enable the General &#8594; Commands option. It worked.

But it turned out to be that, everytime when I start Ubuntu, icons on my desktop will not show up. I will have to manually open a nautilus process to "call up" the desktop icons.

I suspect it's something between Metacity & Compiz settings never working perfectly, but I have the least of the clue on how to fix it.

So if anyone knows of a solution, please help me. Thanks.

---

See [here]("http://ubuntuforums.org/showthread.php?t=1296232") for the original thread.

---

### Post by undecim on 2009-10-21
When you first get to your desktop, open a terminal, and see if the command "pgrep nautilus" gives any output (i.e. a relatively meaningless number)

If its blank, then a temporary solution might be to add "nautilus -n" as a startup application. and if that doesn't work, just try "nautilus" (without the "-n")

---

### Post by Gias Kay on 2009-10-22
The workaround does work. Thanks.

But I still believe this is caused by some config problem at its root, and I have no idea where it is.

---

### Post by Gias Kay on 2009-11-11
Hi, there is one minor problem if using this workaround, that is upon the desktop's fresh load-up, the first time you double-click an icon or a fold, nothing will happen. You need double-click again for any action to commence. Any ideas?

---

### Post by Peter09 on 2009-11-11
Try deleting the .nautilus folders, this will reset your settings for nautilus. To make sure it works remove the start up of nautilus from the startup setup. 

You could also try deleting the .gnome2 directory to complety reset you gnome settings.

---

