---
title: "Error mounting through sshfs at startup"
date: 2010-09-27
forum: General Help
---

### Post by pmatos on 2010-09-27
I have the following line in fstab:
```
sshfs#pm18@alma.csr.com:/home/pm18	/localhome/pmatos/alma	fuse	users	0	0
```

Now, the interesting thing is that when I start the PC, it tells me it failed to mount and asks me if I want to skip (press S) or to do something else. I always skip.

Then I can go into my desktop and do `mount alma` and it works.

Any ideas why it is not able to mount during boot but afterwards its ok?

Cheers,

Paulo Matos

---

### Post by bilkay on 2010-10-27
It sounds like the mount attempt comes before the network is activated. Try adding the "bootwait" option.

---

