---
title: "dpkg-reconfigure xserver-xorg"
date: 2010-03-04
forum: General Help
---

### Post by uncleBez on 2010-03-04
Have weird troubles with X.

one the window manager doesn't appear to be working (I have no 
window borders.)

When I run dpkg-reconfigure xserver-xorg it doesn nothing. just lingers 10secs then drops back to command prompt? 

Anyone?

---

### Post by tgalati4 on 2010-03-04
cat /etc/X11/xorg.conf

Try renaming it:

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.bad

startx

---

### Post by uncleBez on 2010-03-05
ok. I think i tried that. but I am going to do it again right now.
just to be sure.

Thanks

---

### Post by flippo on 2010-03-05
The window manager is not necessarily a xorg issue.  Can you launch it after boot? (open terminal and type "metacity &")

If so, then your troubles are most likely not xorg related.

---

### Post by uncleBez on 2010-03-05
no luck on that front. wont start X at all now.

---

### Post by uncleBez on 2010-03-05
> **flippo said:**
> The window manager is not necessarily a xorg issue.  Can you launch it after boot? (open terminal and type "metacity &")

When I was in X (without the window manager) I did open a terminal, however it just remained as a white box. I never got a prompt come up in it).

So I couldn't launch it.
I did hit alt-f2 to open the run application dialog and I typed metacity in
that. but nothing happened.

---

### Post by uncleBez on 2010-03-05
So if I run the ubuntu installation on that machine again. will it preserve my home directory?

---

### Post by tgalati4 on 2010-03-05
Yes,  but make sure FORMAT? is unchecked in the partitioner.  Back up your data with  the live CD  first, before installing.

---

