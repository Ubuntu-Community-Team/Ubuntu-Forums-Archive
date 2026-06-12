---
title: "Root terminal question"
date: 2009-08-10
forum: General Help
---

### Post by AoA Linux on 2009-08-10
This is probably a noob question, but I am curious.  What is the difference between running "sudo -i" and "su" in a terminal to become root?

Thanks

---

### Post by cwbar_1 on 2009-08-10
Type man "and your command" in a terminal.  It will tell all!

---

### Post by AoA Linux on 2009-08-10
Thanks.  Found what I wanted to know.

---

### Post by Iowan on 2009-08-10
There are sure to be better answers following, but I discovered that **su** doesn't work with root account disabled - the standard configuration for Ubuntu. Can't say I've tried many **sudo** options.

---

### Post by aysiu on 2009-08-10
*su* means "switch user."

If you don't specify a user, it means "switch to root user" and actually prompts you for the root account password and logs you into the root account.

Since Ubuntu does not enable a root login by default, *su* by itself will do nothing.

If you want a persistent root terminal then ```
sudo -i
``` is the way to achieve that in Ubuntu.

---

### Post by overdrank on 2009-08-10
[RootSudo]("https://help.ubuntu.com/community/RootSudo")
 [ Forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=716201")

---

### Post by AoA Linux on 2009-08-10
Thanks for all the answers guys.  That answer was very helpful aysiu.

---

