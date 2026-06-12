---
title: "Replacing Instant-On OS with Ubuntu"
date: 2010-05-31
forum: General Help
---

### Post by Canti.raid on 2010-05-31
Hi there, I just installed Ubuntu and I enjoy it quite a bit, but I was wondering if there is a way to replace my instant-on OS with Ubuntu.

My laptop came with one of these weird things, and it has a button that boots it specifically when the laptop is off. I was wondering if there was a way to make this button instead boot Ubuntu. Obviously this would be extremely cool. The only problem is that I have no idea how to make this happen.

My laptop is an Asus N61JqX, if that helps any. If you need any more technical information to help me, I'll provide it.

---

### Post by sdennie on 2010-05-31
It will really depend on how the instant-on OS is installed.  If it lives as a partition on your hard drive, you *might* be able to resize and change that partition to be an Ubuntu install.  The other possibility (and the more likely one) is that it's stored in a ROM chip.  In which case, you probably couldn't change it easily.  Still, google around and see if you can find someone who has done it.  I don't have that hardware so I'm just posting the most likely outcomes.

---

### Post by Canti.raid on 2010-05-31
It's actually a removable program. It's called ExpressGate, it's not like Splashtop or anything.

---

### Post by sdennie on 2010-06-01
Bizarre.  So, you are saying it's a "program" living on your Windows partition?  If so, it's possible it consists of some sort of superfluous Windows GUI and essentially a disk image of what it should run.  If that's the case, and you can find the disk image, you could try mounting it and see what happens.  Something like:

```

sudo mount -o loop /location/of/image /place/to/mount

```

If that works then, yeah, you can probably figure out how to replace the imagine with Ubuntu without much of a problem.

---

### Post by Spr0k3t on 2010-06-01
There are people who have managed to change the ExpressGate software a little bit... hacking some good bits as well.

[http://www.phoronix.com/forums/showthread.php?t=11610](http://www.phoronix.com/forums/showthread.php?t=11610)

If you are feeling froggy, go for it.  If it breaks your system... can't really help much.

---

