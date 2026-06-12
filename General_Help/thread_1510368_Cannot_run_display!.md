---
title: "Cannot run display!"
date: 2010-06-15
forum: General Help
---

### Post by Hmmster on 2010-06-15
Hi!
So here's the case. I try to boot my computer, it starts, it starts loading ubuntu. But all i get is this full screen terminal thingy prompting me to log in. So i do, and well. There's still just a terminal. I try writing "Nautilus" and get the error that display cannot be run. I try writing "GKSUDO nautilus" and get the same error, with a little difference.

What should i do? D:

---

### Post by Hmmster on 2010-06-15
Bumpity.

---

### Post by WorMzy on 2010-06-15
Try pressing Ctrl+Alt+F7. Press Ctrl+Alt+F1 to get back to the terminal if that just displays a black screen.

If you got a black screen, then run ```
sudo /etc/init.d/gdm start
``` if that gives you an error, make a note of it, then post it here.

---

### Post by Hmmster on 2010-06-15
Hmm, that worked. And i feel really dumb, because i have no idea why. D:
What did that code work? Why didn't it start before?

---

### Post by beowulf1416 on 2010-06-15
that command simply started your display (gdm = gnome display manager). it also means that your display wasn't started up automatically.

is it ok now? is it starting automatically or do you have to type in the command to start it again every time you reboot?

---

