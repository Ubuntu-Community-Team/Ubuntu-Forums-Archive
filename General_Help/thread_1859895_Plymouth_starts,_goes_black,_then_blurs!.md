---
title: "Plymouth starts, goes black, then blurs!"
date: 2011-10-14
forum: General Help
---

### Post by AnarkoNinja on 2011-10-14
Hey everybody.
I have just gotten Plymouth to work (at all) with the Oneiric update... however:
Plymouth works fine when shutting down, looks beautiful and just works.
When I start up, (without FRAMEBUFFER=y) it delays, flashes for a second, and then instantly shows login...
So, I added FRAMEBUFFER=y into /etc/initramfs-tools/conf.d/splash...
Now it lags a second, starts showing for a very brief time, then blurs, almost into a dead Windows kinda thing... colors everywhere... then shows login.
I've downloaded plymouth-manager and played around with different themes and resolutions to no avail. 
Anyone suggestions would be great or let me know if anyone else had experienced this problem!

BTW, I know it's just cosmetic, but plymouth is intended to convince my wife to solely use ubuntu xD)

---

### Post by AnarkoNinja on 2011-10-20
Sorry if my previous post was unclear due to lack of sleep.
Here's my hardware specs:
[INDENT]
Acer Aspire Laptop
Intel i3-370m 2.4GHz x4 Processors
Intel integrated HD Graphics
Intel IronLake Mobile Graphics Driver
64-Bit OS
4GB RAM
[/INDENT]
Here's what's happening with my Plymouth:
First of all, Plymouth works perfectly on shutdown, it's on boot when I have any problems.
I have played around with resolutions and adding FRAMEBUFFER=y to the splash file.

With FRAMEBUFFER=y set, on boot up Plymouth flashes for one second, goes black, and then comes back blurred (as in colors everywhere), stays, then login shows.

Without FRAMEBUFFER=y, screen stays black for a second, Plymouth flashes, and then immediate login screen.

If anyone knows the reason or has experienced similiar problems with this "blur" please let me know. Any solutions or ideas are gratefully welcome. Thanks in advance for your time.

---

### Post by AnarkoNinja on 2011-10-22
thank you so much you guys are freakin awesome. :---)

---

