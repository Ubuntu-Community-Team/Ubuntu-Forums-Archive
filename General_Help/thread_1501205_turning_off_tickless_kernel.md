---
title: "turning off tickless kernel"
date: 2010-06-04
forum: General Help
---

### Post by MattFS218 on 2010-06-04
I'm trying to disable tickless kernel support for Ubuntu 10.4 64-bit. I have added nohz=off to grub and my the kernel options, but when I cat

/boot/config-2.6.27-7-server

it's still showing 

CONFIG_NO_HZ=y

/var/log/messages shows the nohz=off being sent to the kernel at startup, but is there any way to confirm I have correctly turned off tickless support in my kernel? I assumed it should reflect in the /boot file, but maybe I'm mistaken.  Thanks

--matt
[Predictive Dialer]("http://www.hellohunter.com")

---

