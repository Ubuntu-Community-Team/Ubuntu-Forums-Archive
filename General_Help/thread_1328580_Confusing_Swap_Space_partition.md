---
title: "Confusing Swap Space partition"
date: 2009-11-16
forum: General Help
---

### Post by yo2boy on 2009-11-16
It's me again! I just did a fresh-install of 9.10 because I was apparently using ext3 since I upgraded from 9.04

Anyway, I have a slight problem. 

[IMG]http://imgur.com/9ixvS.png[/IMG]

I have 2 swap spaces. I want to remove the one **I'M NOT USING.** And, I don't know which one that is..

So can you guys help?

---

### Post by yo2boy on 2009-11-16
-bump-

---

### Post by audiomick on 2009-11-16
Hallo.
Bear in mind that I am not a Guru;)
As far as I know, Ubuntu uses all the swap space it knows about. I have two on mine, spread across two discs, because I read that that makes it a bit faster. If they are both on ine disc, you don't have any advantage, but they should be both being used.
If your game, you could try starting gparted from the live cd and merging them, but I would be inclined to stick to the old adage of not fixing a running system. Time will come when you do a fresh install. Fix it then.

---

### Post by drs305 on 2009-11-16
The one you are using will be listed in fstab. Take a look at the contents with:
```

gksu gedit /etc/fstab

```

You can compare what is listed there with the following, which will list your current "swap" UUIDs:
```
sudo blkid | grep swap
```

This command will also show what "swap" is currently registered in "resume":
```
cat /etc/initramfs-tools/conf.d/resume
```


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

