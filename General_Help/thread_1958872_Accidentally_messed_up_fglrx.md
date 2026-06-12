---
title: "Accidentally messed up fglrx"
date: 2012-04-15
forum: General Help
---

### Post by bogie5464 on 2012-04-15
Ok so long story short, I messed up my fglrx installation whilst trying to remove a watermark. That's not the problem though. The problem is that now I get no display, obviously. I tried booting into a live distro and chrooting over to my installation, and then aptitude removing and reinstalling fglrx. I may not have done it right though. Any suggestions?

---

### Post by dcstar on 2012-04-15
> **bogie5464 said:**
> Ok so long story short, I messed up my fglrx installation whilst trying to remove a watermark. That's not the problem though. The problem is that now I get no display, obviously. I tried booting into a live distro and chrooting over to my installation, and then aptitude removing and reinstalling fglrx. I may not have done it right though. Any suggestions?

Replace the xorg.conf file with a copy of the failsafe one.

---

