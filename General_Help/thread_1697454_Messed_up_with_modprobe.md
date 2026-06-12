---
title: "Messed up with modprobe"
date: 2011-02-28
forum: General Help
---

### Post by Odexios on 2011-02-28
Hello everyone!

I have a shared netbook , on which we installed Ubuntu 10.10 .

We had some issue with the graphical chip: at first everything worked fine, but after some time we had an error (can't find matching glx visual and similar) that prevented us from playing almost any game on it.

It wasn't really an issue for me, so I just settled with wathever was working. It seems like he tried to solve the issue by himself, and, from what I can see, executed this command:

sudo modprobe i915

Now the graphic is a little dizzy, the brightness can no longer be adjusted, the battery life has halved and so on.

Can I save somehow the situation without reinstalling everything?

---

### Post by blueridgedog on 2011-02-28
Then try

```
sudo modprob -r i915
```

The -r is for "remove".

See the man page for more information:

[http://linux.die.net/man/8/modprobe](http://linux.die.net/man/8/modprobe)

---

### Post by Odexios on 2011-02-28
Already tried; it says that the driver is in use.

I tried to close X (via /etc/init.d/gdm stop) but nothing changed.

---

### Post by blueridgedog on 2011-03-01
Try creating a blacklist entry for the module and then restart:

[http://ubuntuforums.org/showthread.php?t=166624](http://ubuntuforums.org/showthread.php?t=166624)

---

### Post by Odexios on 2011-03-01
Thanks, it worked fine!

---

