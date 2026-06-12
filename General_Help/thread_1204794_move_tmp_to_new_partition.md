---
title: "move /tmp to new partition"
date: 2009-07-05
forum: General Help
---

### Post by fboecom on 2009-07-05
I have created a 9.04 install with a separate /tmp partition. I changed my mind and wanted to have tmp on another partition. With some intermediate steps, the fstab is now mounting the new partition as /tmp and the old tmp partition as /test. In safe mode I copied everything out of /test into /tmp following an instruction I found in this forum (on moving the /home directory):

```
cd /test
find . -depth -print0 | cpio --null --sparse -pvd /tmp

```
that worked well, the two directories look the same. When I boot in normal mode, I can login, but immediately get an error message, of which the details are:

> /etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=nl_NL.
Setting IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinit.d/default.
mkdtemp: private socket dir: Permission denied

what do I have to do to move /tmp in the right way?

---

### Post by geirha on 2009-07-05
Have you set the correct permissions on your new /tmp?
```
sudo chmod 1777 /tmp
```

---

### Post by fboecom on 2009-07-05
..and that was all it took to get my ubuntu desktop back again!!
Thanks geirha!

(command executed in recovery mode console)

---

