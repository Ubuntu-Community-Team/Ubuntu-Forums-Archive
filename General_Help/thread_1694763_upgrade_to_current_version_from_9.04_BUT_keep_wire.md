---
title: "upgrade to current version from 9.04 BUT keep wireless driver the same"
date: 2011-02-24
forum: General Help
---

### Post by PUPPY?123 on 2011-02-24
Xubuntu 9.04 installs the drivers for my wireless pci card on my desktop perfectly.  Whenever I update to a newer version, the wireless disappears.  I would like to use 10.10 but obviously internet is very important.

Can I tell it to keep the same driver?  I actually don't really know what the specific driver it is.  If this is relevant info, please instruct me how to give it to you.

Thanks.

---

### Post by PUPPY?123 on 2011-02-25
BUMP.  PLEASE HELP.  :cry::cry::cry::cry::cry::cry:

---

### Post by aeiah on 2011-02-25
the driver will either be built into the kernel or loaded as a module. when you compile a module, you compile it against your current kernel. 

whilst its perhaps possible to install 10.10 and compile an old kernel for it, it isn't a very good idea, and would require more work than just compiling the driver for 10.10 in the first place.

you should make a note of your wireless chipset and do some google searches. you'll probably find there's a way to fix it.

---

### Post by Bcrowes11 on 2011-02-25
If you have an ethernet cord (as i did) Then install the new version, then got to additional drivers and it should detect it and install it.:popcorn:

---

### Post by PUPPY?123 on 2011-02-25
Thanks for responses.  It kind of annoys me that the kernel got worse for my machine.  But what can you do?  I think I'll try to find a windows driver and use ndiswrapper.  Connecting that computer using an ethernet cord is a headache.  That's why I use wireless.  I had have to unplug everything and move it quite a way then move it back.  I'm not even sure what driver to get...the linux driver seems to have become defective..though I'm not sure since I'm no expert.

---

### Post by Bcrowes11 on 2011-02-25
Best of luck....:(

---

