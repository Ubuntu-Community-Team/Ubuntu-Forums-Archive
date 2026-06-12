---
title: "Any way to disable syndaemon?"
date: 2010-03-17
forum: General Help
---

### Post by spyrule on 2010-03-17
Syndaemon is the service that makes the track pad stop responding for X number of seconds while, and shortly after typing.

I know this is handy for a lot of people, but I don't really bump the touchpad while typing (maybe I'm typing wrong).

So sometimes I'm trying to bounce back and forth between keyboard and trackpad really quickly but the mouse will stay stuck for just a second and then release. I found that I can decrease the amount of time that the daemon holds onto the mouse by entering the following command:

```
syndaemon -d -i 0.1s
```

But, every time I reboot I have to do this again... And there's still a little lag.

Is there anyway to stop this service from running without stopping my trackpad all together?

---

### Post by Ozymandias_117 on 2010-03-18
I don't see how disabling it could hurt anything.

First place I would look for trying to disable it, is System -> Preferences -> Startup Applications

If it's not in there, you can try making a copy of syndaemon somewhere and then just removing it from /usr/bin - If it DOES screw up your touchpad, use a liveCD to copy the file back to /usr/bin.

This may not be the best way... but it's all I can think of for you to try.

---

### Post by spyrule on 2010-03-18
Thanks for the response Ozymandias_117!

I didn't realize that that's where the daemon would load from, so, I just moved it from /usr/bin/syndaemon to /home/user/Documents/syndaemonBAK ... Seems to work okay so far, thanks!

---

### Post by jiaguilera on 2010-03-20
I think I've found another solution (works for Lucid)

Into "System > Preferences > Mouse" find Touchpad tab.
Unchecking "Disable touchpad while typing" option makes syndaemon stop running.

---

### Post by stoyanmihaylov on 2011-04-16
That worked for me too. After my upgrade to 11.4, I got couple of problems - Ubuntu Unity plugin - fortunately I had chance to stop it from CompizConfig. I missed Panels - and I did one shortcut on desktop - to start gnome-panels, there were 2 daemons who garbed 200% from processor - every one took one of cores (2 cores total).  frameworkd - I uninstalled it and syndaemon. I stopped - thanks to this post.
Now I have new looking old panels, which I like, use etc. New unity is very nice, but I want to have full control over content of panels. Hope before somebody remove panels - new unity will get all features and will allow full (easy) control from user.

---

