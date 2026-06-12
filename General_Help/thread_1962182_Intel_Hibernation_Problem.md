---
title: "Intel Hibernation Problem"
date: 2012-04-20
forum: General Help
---

### Post by Kodeine on 2012-04-20
Salutations!

So after upgrading to kernel version '3.2.0-17-generic' I'm experciening some problems upon attempting to hibernate. I'd say one in ten times, so it doesn't always happen, it freezes upon seeing the CLI screen where it states the various things it's doing to go into hibernation. In total it's happened four times. I scooted around Google and found this article which may be the problem as I do use my i5's on-board graphics.

[http://www.h-online.com/open/features/Kernel-Log-Intel-hibernate-bug-fixed-1503282.html](http://www.h-online.com/open/features/Kernel-Log-Intel-hibernate-bug-fixed-1503282.html)

But the article states it's been fixed in previous versions of the Linux kernel? Anyone know what the problem might be?

Thanks bye!

---

### Post by for.i.am.root on 2012-04-20
How much swap do you have and how much RAM?

Your swap *should* be double your RAM. When you hibernate everything in RAM is moved into swap. If your swap isn't large enough it can cause problems.

Potential:
Due to the issue being intermittent and not consistent. Sometimes you have more going on and hence are using more RAM, requiring more swap to hibernate.

---

### Post by Kodeine on 2012-04-20
> **for.i.am.root said:**
> How much swap do you have and how much RAM?

Your swap *should* be double your RAM. When you hibernate everything in RAM is moved into swap. If your swap isn't large enough it can cause problems.

Potential:
Due to the issue being intermittent and not consistent. Sometimes you have more going on and hence are using more RAM, requiring more swap to hibernate.

According to system monitor I have 3GB of RAM whilst having 4GB of swap. I already close everything down before going into hibernation but I'll try waiting for several seconds after doing such and see if that helps.

---

