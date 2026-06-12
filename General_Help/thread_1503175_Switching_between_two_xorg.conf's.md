---
title: "Switching between two xorg.conf's"
date: 2010-06-06
forum: General Help
---

### Post by abel_bcn on 2010-06-06
Hi all,

I've got an i5 Macbook Pro, on which I've got Ubuntu 10.04, which I use 90% of the time (mainly for work).

I've added a few lines to xorg.conf to make the graphic card run cooler and thus get some more battery life. Sometimes, though, I do need full graphic potential, for which I have another xorg.conf prepared without those lines, so I can switch back and forth when I need it.

Currently, to change back and forth, I rename the files accordingly and reboot, which is a pain in the neck. I tried restarting gdm after switching files instead but it didn't quite work (maybe I wasn't doing it correctly).

So, fellow experts, what's the easiest and fastest way to switch between two different X11 config files?

Thanks in advance!

---

### Post by abel_bcn on 2010-06-07
I found this script to restart X, but after switching to the desired xorg.conf and running it I get the same results.

```
#!/bin/sh
sudo kill `cat /tmp/.X0-lock`
startx
~$ nohup RestartX.sh
```

I'm having to reboot instead to make it work. Any ideas on a faster method?

---

