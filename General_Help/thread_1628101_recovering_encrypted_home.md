---
title: "recovering encrypted home"
date: 2010-11-22
forum: General Help
---

### Post by phoenix137 on 2010-11-22
Dummy me let root run out of space because I didn't know to use logrotate.  I was able to compress the system logs but not before the damage was done me thinks; now the computer is unbootable.

I booted from a LiveCD and got my old partitions mounted under /media/oldroot to try and recover files; however, I forgot that I had encrypted my home.  I found [http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html) and was following it; however, I seem to run into a bunch of path issues after I chroot.  

The chroot command returns:
bash: groups: command not found

The su command returns:
-su: cut: command not found
-su: getent: command not found
-su: expr: command not found
-su: groups: command not found

Finally, the ecryptfs-mount-private command returns:
-su: ecryptfs-mount-private: command not found

I have separate partitons for /, /home, /tmp, /usr, and /usr/local and bothered to mount the first 2.  (If only I had been ambitious enough to create a /var *sigh*)

I was running Ubuntu 10.10.

---

### Post by phoenix137 on 2010-11-22
hehee... that last sentence was telling.  I mounted /usr (duh) and my path problem was fixed!

I AM HOME!!!  WOOT!!!

:popcorn:

---

