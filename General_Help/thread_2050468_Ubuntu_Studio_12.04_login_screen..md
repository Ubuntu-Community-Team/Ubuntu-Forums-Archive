---
title: "Ubuntu Studio 12.04 login screen."
date: 2012-08-30
forum: General Help
---

### Post by kratanuva on 2012-08-30
Hey guys, I'm new here, but I've been using Ubuntu for a few months now and I use it 90% of the time. I installed ubuntu studio 12.04 on my laptop, and that has been my main operating system for awhile now, and after trying various different desktop environments Unity is the one that stuck, (don't judge me! :p) but I still have the ubuntu studio log on screen, and I personally think it's kind of ugly, but I'd hate to have to start from scratch with a vanilla Ubuntu install just to have the standard Ubuntu 12.04 login screen.

Anyway, I've been trying to google solutions for this, but everything I've tried has come up dry. I guess either all the articles I'm finding are outdated, or that for some reason they don't apply to Ubuntu Studio...

So yeah, any help on getting the standard Ubuntu login screen would be awesome, thanks!

---

### Post by kratanuva on 2012-08-31
bump

---

### Post by gman101 on 2012-08-31
open terminal and type 

sudo dpkg-reconfigure gdm/lightdm/xdm

choose _dm depending on what your current login screen is, its probably lightdm so type

sudo dpkg-reconfigure lightdm

---

