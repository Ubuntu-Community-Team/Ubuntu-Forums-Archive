---
title: "Can't Overlock in Ubuntu?"
date: 2010-10-24
forum: General Help
---

### Post by maximus20895 on 2010-10-24
I recently switch from Windows 7 to Ubuntu 10.04 and then to 10.10. When I had Windows 7 running I was overclocking via manual settings in my BIOS. I am almost positive I had the same overclocking settings in my BIOS when I had 10.04 as well.

For some reason though when I use the same settings with 10.10 it tries to but up, but it just says it will restart in 30 seconds. I have no idea why. I know the overclock is stable as I have been using it for a year or more. This seems to just happen when I got 10.10.

Any ideas this would happen? 

Thanks. :)

---

### Post by WorMzy on 2010-10-24
I've used Ubuntu on an overclocked machine before with no problems, so I couldn't say why it's not working for you. Can you boot from a LiveCD while the system is overclocked? If so, then check your installed version's error logs (I believe Ubuntu has a log viewer application under System -> Administration, or possibly Applications -> Accessories. Failing that, just look in the /var/log folder). dmesg.log may have some useful information. errors.log, kernel.log and maybe even syslog.log may also have some info.

---

### Post by maximus20895 on 2010-10-24
Alright, I will check that. Thanks!

---

