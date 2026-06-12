---
title: "Wireless adapter detection"
date: 2011-01-17
forum: General Help
---

### Post by amshank on 2011-01-17
Hi,

I'm running maverick on a laptop with a wireless adapter which you can turn on and off via a button above the keyboard.

If you boot ubuntu with it switched on, everything works fine, you can turn it on and off and ubuntu detects when it is on or off.

However if you boot with it off and then subsequently turn it on then ubuntu doesn't detect it and you require a restart for it to work.

Is there a way to force ubuntu to check for the hardware after boot and discover the new adapter in the same way that it does during a normal boot?

Thanks,

---

### Post by lithopsian on 2011-01-17
udevadm trigger would probably do it.

---

