---
title: "How to stop the window manager changing its appearance"
date: 2011-07-18
forum: General Help
---

### Post by Jim_in_Germany on 2011-07-18
Hi,

When I start Ubuntu, file explorer windows look like they should.

Then, after about 15 seconds, the windows manager automatically switches to a greyer, bulkier design

How can I stop this behaviour?
I am using Ubuntu 11.04 as a guest OS in Virtual Box 4.0.12

Thanks in advance.

---

### Post by CatKiller on 2011-07-18
It's because gnome-settings-daemon has crashed. You can restart it, but that doesn't bring the folder icons back (it corrects all the other themeable elements though). If you want the folder icons to come back you need to log out and log back in.

---

### Post by Jim_in_Germany on 2011-07-18
I tried entering "sudo gnome-settings-daemon restart" and this restored some of the settings.
However, you are correct. The folder icons are still gone and if I log out, then log back in the gnome-settings-daemon crashes after a few seconds (as described above), so I am back to square one.

I would be grateful for any more suggestions.

---

### Post by CatKiller on 2011-07-18
> **Jim_in_Germany said:**
> I'm afraid this happens every time I boot Ubuntu, so logging in and out just results in the above behaviour.

Sorry, I missed that part of your post.

> Could you give me any more info on the gnome-settings-daemon.
How might I restart this?Alt-F2 will give you the Run dialogue box. Then you just write gnome-settings-daemon in the box and hit Run.

This is fine when it only happens every now-and-then, but for troubleshooting purposes you'd probably want to run it in a Terminal (Applications -> Accessories -> Terminal) so that you get to see any error messages it might give about why it's crashing.

EDIT: According to its manpage, g-s-d also has a debug mode which could perhaps give more information.```
gnome-settings-daemon --debug
```

---

### Post by Jim_in_Germany on 2011-07-18
Debug didn't yield any additional information, so I wrote a small shell script and have it start with Ubuntu.

Although this is a dirty hack and doesn't solve the original problem, it works.

In case it helps anyone else:

sleep 30
killall gnome-settings-daemon
/usr/lib/gnome-settings-daemon/gnome-settings-daemon
sleep 2
nautilus -q

Thanks for your help and for pointing me in the right direction

---

### Post by CatKiller on 2011-07-18
Glad you got it sorted.

---

