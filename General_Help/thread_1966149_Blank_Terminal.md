---
title: "Blank Terminal"
date: 2012-04-26
forum: General Help
---

### Post by merlinus on 2012-04-26
When I open a terminal in 12.04, there is no system prompt, just a blank window.

---

### Post by papibe on 2012-04-26
Hi merlinus.

Unfortunately I haven't had the time yet to install 12.04 yet, but I have seen this kind of errors before.

By any chance have you customized your .bashrc?
What happens if you press Ctrl+C ?
In case you get a prompt from the last one, what happens if you run 'bash'?

Regards.

---

### Post by merlinus on 2012-04-26
Nothing happens when I press Ctrl+c.

I changed the default theme, though, and now I can see text.  But I cannot use my dark themes anymore!

---

### Post by papibe on 2012-04-26
Try this to recover the terminal:

Press Alt+Ctrl+F1 to goto text mode, and login (if that does not work, you will have to boot into recovery mode).

Rename your current bashrc:
```
mv  ~/.bashrc  ~/.bashrc.bak
```
Then copy the system template back to your home (as a fresh install):
```
cp  /etc/skel/.bashrc ~/
```
Press Alt+Ctrl+F7 to go back to GUI from text mode.

I hope that helps, and tell us how it goes.
Regards.

---

