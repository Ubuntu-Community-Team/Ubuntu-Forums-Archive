---
title: "Compiz Wallpaper Plugin Broken with 10.10"
date: 2010-10-13
forum: General Help
---

### Post by Groucho Marxist on 2010-10-13
After upgrading from 10.04 to 10.10, I've noticed (as have others) that the Compiz plugin for multiple wallpapers on different desktops is broken. If I wish to move to a new screen with the Expo feature, the graphics behave oddly (i.e. things become blurry or windows look terrible). I found a work-around on [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/629391"), but this is only a temporary fix to a long-term solution. Has anyone else here had this problem or figured out a way to solve it?

---

### Post by Jorin on 2010-10-18
I've had the same problem since upgrading to 10.10. As soon as I enable the Wallpaper plugin I get leftover images of various window states on my desktop. 

It looks a lot like this: [http://i.imgur.com/MPfvP.png](http://i.imgur.com/MPfvP.png)

The workaround on Launchpad didn't help me either. Looks like they are working on a fix, so keep us posted! :)

---

### Post by ubername on 2010-10-18
Make sure you have compiz-fusion-plugins-extra installed. It is not installed by default any more.

```
sudo apt-get install compiz-fusion-plugins-extra 
```

---

### Post by Obscura on 2010-10-25
Same problem here and compiz-fusion-plugins-extra is already the newest version.

---

### Post by Groucho Marxist on 2010-11-09
> **ubername said:**
> Make sure you have compiz-fusion-plugins-extra installed. It is not installed by default any more.

```
sudo apt-get install compiz-fusion-plugins-extra 
```

I just checked and I've already installed it. 
This is a most perplexing problem :(

---

### Post by hackerseraph on 2010-11-13
any updates on this bug?

---

### Post by rockachu2 on 2010-12-02
the fix is being implemented into x, or maybe into fusion-plugins-extra.

a temporary workaround is to switch to tty and back which causes the wallpapers plugin to start drawing again.

bug report:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/629391]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/629391")

;)

---

### Post by Miyth on 2011-01-22
Has there been any headway on this? I just updated to Mavrick today (yes I know, I'm late on the uptake) and this bug is horrible. I've been looking for a fix but can't find anything permanent.

---

### Post by Buying_Some_Time on 2011-02-04
Bump, the workaround only works until you restart. Anything new on this?

---

