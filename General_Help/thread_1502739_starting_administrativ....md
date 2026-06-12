---
title: "starting administrativ..."
date: 2010-06-05
forum: General Help
---

### Post by eric1234 on 2010-06-05
I have ubuntu 10.04. The installation is about 3 days old.
My account type is administrator.

When I try to open "synaptic package manager," "root terminal," "software sources," or "firewall configuration" the window list on the panel on the bottom of the screen informs me "starting administrativ..." and then vanishes without fanfare. Clearly it would seem these programs are all dependent on something I managed to screw up.

The question then is; what is it, and how can I fix it?

Also note: everything works fine on the root account.

---

### Post by stderr on 2010-06-06
Hi Eric.

Ubuntu's trying to run /usr/bin/gksu to present a password prompt. Can you try opening gnome-terminal (Applications->Accessories->Terminal) and running this (it tries to open a password window, in debug mode, and we pass it the name of a non-existent program as a simple test):

```
gksu -d thx1138
```

Hopefully that might spew out some useful debug messages in the terminal - post anything you get back here (it's "Shift + Ctrl + C" to copy selected text from a gnome-terminal window).

---

### Post by eric1234 on 2010-06-06
Fantastic news; I fixed everything a couple moments before rechecking this thread. It turned out I had set etc/sudoers.d/README permission to 0640 rather than 0440. Undoing this fixed everything. So now there are two potential solutions to any future users with this problem that find this thread.

Also, much thanks to you, stderr.

---

