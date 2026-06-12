---
title: "Setting ~user directory in another hard drive?"
date: 2010-06-26
forum: General Help
---

### Post by Nugar on 2010-06-26
Hello all,

Some time ago, I read somewhere that you can set your ~user directory in a separate partition. This would allow you to upgrade or even clean install without overwriting it.

My question is whether this could be done but using a secondary hard drive. 

Is it possible? Can someone direct me to any howto on this?

Thanks in advance,

---

### Post by supergrav on 2010-06-26
It is possible to use another physical drive as your /home partition. When you install your OS you have a choice to manually partition disks on your system. There you can specify where /home partition should be mounted, as long as other options, like creating another partition just for grub for example.

---

### Post by warfacegod on 2010-06-26
If you don't want to go the fresh install route right now, this may get you fixed up nicely. [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Nugar on 2010-06-26
Thanks a lot guys! I'll start my reading right away.

---

### Post by henrydubb on 2010-06-26
> **Nugar said:**
> 
My question is whether this could be done but using a secondary hard drive. 

Is it possible? Can someone direct me to any howto on this?

Thanks in advance,

It is certainly possible. I did before. It was fine at first and then I remember problems. When it worked it treated both hard drive as one file system. Overtime I had problem loading home at startup. This could have been the result of an old hard drive, but I found it was not the optimal setup. 

I think it also had something to do with my permissions. For example, when I booted up I need to put admin password in to mount other hard drive. If I had home on this drive one can see how problems might result.

---

### Post by warfacegod on 2010-06-26
> **henrydubb said:**
> It is certainly possible. I did before. It was fine at first and then I remember problems. When it worked it treated both hard drive as one file system. Overtime I had problem loading home at startup. This could have been the result of an old hard drive, but I found it was not the optimal setup. 

I think it also had something to do with my permissions. For example, when I booted up I need to put admin password in to mount other hard drive. If I had home on this drive one can see how problems might result.

During a fresh install, at least, a second HDD as /home will auto-mount on bootup.

---

