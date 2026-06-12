---
title: "xorg issue installing 10,04"
date: 2010-05-09
forum: General Help
---

### Post by unplugged23 on 2010-05-09
Hi guys,

I'm trying to install 10.04, but have hit a few bumps. The first time I tried to boot the live cd, the monitor frequency would go out of range. I fixed this by deleting the ```
ro quiet splash
``` from the end of the boot line, and replacing it with ```
ro vga=773 nomodeset
```. After booting with this modification to the kernel line, rather than booting into the live cd desktop, it takes me to a command setting. To try and get things moving I type ```
startx
```It will run through some code and eventually come up with ```
fatal server error: no screens found
``` I'm not exactly sure what the problem is, but I suspect that it's with the xorg.conf file. Could someone please explain what's going on and how to fix it?

Thanks for any help!

---

### Post by James78 on 2010-05-09
Well, my friend had this problem too with an ATI card and some monitor, I suspect it was the monitor and a bug/issue and not the card. He said that updating from the repos seemed to fix it. But anyways, using an Xorg config could help to stabilize the issue. Try doing 'sudo Xorg -configure', remember that you cannot use this command while Xorg or an Xsession is running, so I suggest booting into the recovery mode, going into the console and doing it, just takes like 45 seconds more.

Generating a Xorg configuration from root typically sets the file in /root/Xorg.conf.new or something similar, so you might have to copy the file there to /etc/X11/xorg.conf

---

### Post by unplugged23 on 2010-05-09
Thanks, I'll give that a go. I actually started downloading 9.10 right after I posted this, to try and do a repo upgrade. Hopefully I can get this working some how.

---

### Post by unplugged23 on 2010-05-09
I can't get into an X session, hence this post. Like a said, the cd is putting me into a command interface anyways. I just tried sudo Xorg -configure, it spit out a bunch of stuff, and at the end says 'configuration failed'. I'm going to try updating fromt he repo's

---

### Post by Catharsis on 2010-05-10
> **unplugged23 said:**
> I can't get into an X session, hence this post. Like a said, the cd is putting me into a command interface anyways. I just tried sudo Xorg -configure, it spit out a bunch of stuff, and at the end says 'configuration failed'. I'm going to try updating fromt he repo's

I...wouldn't suggest that. The LiveCD is generally a good predictor of what the install will be like, so you'll most likely get the same problem after you upgrade from Karmic. And then you'll lose your working install and be left with only a Karmic LiveCD to work with.

---

### Post by James78 on 2010-05-10
Oh, I didn't mean update the distribution lol, I meant just update any packages that need updating.

---

