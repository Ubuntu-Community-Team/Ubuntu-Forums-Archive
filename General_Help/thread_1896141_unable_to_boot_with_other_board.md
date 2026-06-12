---
title: "unable to boot with other board"
date: 2011-12-16
forum: General Help
---

### Post by Rocky73 on 2011-12-16
Im a newby to linux. I had an edubuntu server 7.04 installed in a computer with video card. unfortunately the card had a problem that rendered the system not to boot. no display is seen. i tried it to other mobo with built in video card, unfortunately the same does not work. it seems that it has a problem on display. how can i fix it to recover root file which is very important. anyone who can help me please?

---

### Post by dcstar on 2011-12-17
> **Rocky73 said:**
> Im a newby to linux. I had an edubuntu server 7.04 installed in a computer with video card. unfortunately the card had a problem that rendered the system not to boot. no display is seen. i tried it to other mobo with built in video card, unfortunately the same does not work. it seems that it has a problem on display. how can i fix it to recover root file which is very important. anyone who can help me please?

You just cannot move from one hardware platform to another and expect an existing system to work. You might be able to manually edit the xorg.conf file but that only applies to desktop GUI systems, not servers.

Boot off a Live CD and copy the data off the hard disk. There are many detailed instructions on this already in the forums.

---

