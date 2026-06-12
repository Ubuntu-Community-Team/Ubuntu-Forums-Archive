---
title: "Linux partition corrupted"
date: 2010-05-13
forum: General Help
---

### Post by Mr Nemo on 2010-05-13
I have no idea how I did it. All of a sudden I couldn't access synaptic so I restarted my system and the login screen wouldn't show up. I tried dpkg --configure -a and sudo apt-get install -f. I can't access my system at all. Any way to fix this?

---

### Post by MooPi on 2010-05-13
Boot from a live CD and run ```
e2fsck -n
``` This will reveal if your file system has really corrupted.If it finds errors then run ```
e2fsck -p
```
You may also have to update grub if as you stated the boot menu not showing.

---

### Post by Mr Nemo on 2010-05-13
the boot menu does show. The ubuntu login screen does not display. Going to try this now be back in a few. (hopefully on ubuntu)

---

### Post by Mr Nemo on 2010-05-13
The filesystem itself seems fine. I can't get into synaptic or log in. Is there any way to save the system or do I need to reinstall?

---

### Post by MooPi on 2010-05-15
You haven't mentioned if you can use command line for package management. Can you use apt-get from terminal ? And it seems as if GDM may be corrupted from your description. Sorry I didn't pick up on this before.

---

### Post by Mr Nemo on 2010-05-16
No, I wasn't able to use apt from the terminal. I think I just fried my system somehow... I'm not really sure what I did. Thanks for your help though.

---

