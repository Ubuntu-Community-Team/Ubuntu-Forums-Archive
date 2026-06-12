---
title: "Startup scripts."
date: 2009-07-14
forum: General Help
---

### Post by t0mppa on 2009-07-14
Ok, since System / Preferences / Session was taken out of Jaunty, I figured it wouldn't hurt to educate myself and do this manually. So I wrote a simple script to disable my touchpad while typing and added it to be started on run levels 2-5 with update-rc.d, but the problem I'm facing is that it's not being run. Or alternatively, it gets killed at some point before I manage to login to X.

Contents of the file:```
$ cat touchpad-fix.sh
#! /bin/bash
syndaemon -i 3 -d
```

It is executable:```
/etc/init.d$ ls -la | grep touchpad-fix.sh 
-rwxr-xr-x   1 tommi tommi    32 2009-07-10 18:12 touchpad-fix.sh
```

And it is added to the rcS.d directories: ```
/etc/rc2.d$ ls -la | grep touch
lrwxrwxrwx   1 root root    25 2009-07-10 18:23 S99touchpad-fix.sh -> ../init.d/touchpad-fix.sh
```

If I run it manually, it works just fine and sticks in there until the next boot, but I'm a little confused as to why the above steps haven't automatized it. Did Ubuntu switch completely to Upstart like the early plan was (by Ibex), so the scripts have to made event based rather than runlevel based?

And yes, I could just put the syndaemon line to rc.local instead, but from what I read, this was the Ubuntu way, plus I'm curious why it's not working.

---

### Post by geirha on 2009-07-14
I'm not familiar with syndaemon, but my guess is that it requires a running X server to connect to, and will simply fail if there isn't one. Also, running it from init is far from the same as running it with System -> Preferences -> Sesssions (which btw is System -> Preferences -> Startup Applications in Jaunty).

When you run it from init, it is also run as root, while if you add it to your startup applications, it will be run each time you log in, and as your user.

---

### Post by t0mppa on 2009-07-14
Oh right, Startup Applications, silly me.

Since GDM is started at 30 on runlevels 2-5 and I put the script at 99, shouldn't X already be running by the time it's executed?

And what's wrong with running it as root? Shouldn't it be better to keep it alive than to reload it every time there's a change of user?

---

### Post by geirha on 2009-07-15
> **t0mppa said:**
> 
Since GDM is started at 30 on runlevels 2-5 and I put the script at 99, shouldn't X already be running by the time it's executed?


It will not automatically connect to any running X server, it will expect you to tell it which X server to connect to, either by a command-line option, or through the DISPLAY environment variable. That won't be set before you log in.

> **t0mppa said:**
> 
And what's wrong with running it as root? Shouldn't it be better to keep it alive than to reload it every time there's a change of user?

Completely depends on the program; whether it is designed to be run as root or as a user. Since you have run it as a user in the past, it is likely it is supposed to run as a user. The man-page for the program would be the best thing to read to find out though.

```
man syndaemon
```

---

### Post by t0mppa on 2009-07-16
Allright, thanks for the explanations. I'll just move it to Startup Applications.

---

