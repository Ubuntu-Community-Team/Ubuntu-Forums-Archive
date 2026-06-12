---
title: "can't log in?!?"
date: 2009-09-05
forum: General Help
---

### Post by Kristofer Van Orton on 2009-09-05
Well when I try to log in it pretty much says I don't have enough disk space and its not possible to log in?!
Has anyone had to deal with this before?
please help?!?

---

### Post by Kristofer Van Orton on 2009-09-05
I can't log in....can't anyone help?

---

### Post by JC Cheloven on 2009-09-05
It would be nice if you could provide a more precise info about your problem. I (have to) imagine that you areexperiencing something like this:

You use jaunty, you push the power button, the login screen appears, you provide your username and password, then a popup window says that you're out of disk space. And you're pretty sure that you have disk space, and perhaps you used to login with no problems before (??).

If the avobe is right (or approximate), you could try one or both of these:
--> Start a live cd session, visit your ubuntu partition with nautilus and check out the free space. If you are actually short of space, consider resizing partitons with gparted (come back with the output of sudo fdisk -l if you need help on that point).
--> Start in failsafe mode (from grub's options), and try the clean option, and/or the fsck option.

Come back with more precise info in you need further advice ;-)

---

### Post by c0mput3r_n3rD on 2009-09-05
You might not have enough linux-swap. Check that out when you boot from livecd

---

