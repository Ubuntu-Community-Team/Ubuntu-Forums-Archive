---
title: "tty sessions gone"
date: 2010-01-18
forum: General Help
---

### Post by moody_mark on 2010-01-18
Hi, Ive recently been removing some packages off my machine and wether its due to that or due to a recent update, ive lost all the tty sessions apart from the default tty7 which hosts the ubuntu desktop. Its likely the former of these two. I do know that I managed to screw up the gnome desktop somehow and had to use the following command to get it back;

```
sudo aptitude install ubuntu-desktop
```

This was when the TTY sessions were working of course.

Does anyone know which package i required to start these sessions? The command below shows i have no TTYs running

```
$ ps aux | grep tty
root      1129  0.1  2.3  27484 11872 tty7     Ss+  11:53   0:16 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-BldYq9/database -nolisten tcp vt7
curtis    1857  0.0  0.1   3044   788 pts/0    R+   16:10   0:00 grep tty
```

Thanks

---

### Post by moody_mark on 2010-01-21
Can anyone help with this problem at all please?

---

### Post by moody_mark on 2010-01-27
Does anyone have any suggestions at all?

---

### Post by moody_mark on 2010-02-01
Well, its not an ideal solution by any means, but on the particular PC in question I had to add a winXP partition, which meant re-installing from scratch, I only had the original winXP image cd so that meant the whole disc got wiped. I re-installed ubuntu 9.10 after into its own partition and its all running smoothly now.

So, problem solved... but not the most ideal way.

---

### Post by Garonenur on 2010-03-01
Hi,  reading this makes me think to do exactly that. reinstall everything.  I hav ethe same problem here, no tty and there are all of them if I boot from USB.  I thought it was a problem with graphics.

---

