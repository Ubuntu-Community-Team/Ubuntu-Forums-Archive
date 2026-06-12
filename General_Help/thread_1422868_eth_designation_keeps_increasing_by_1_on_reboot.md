---
title: "eth designation keeps increasing by 1 on reboot"
date: 2010-03-05
forum: General Help
---

### Post by |{urse on 2010-03-05
So the thread title kinda sums it up. If i have eth186 and i reboot I have to open wicd and change it to eth187 get connectivity. I'm currently at eth200 so this has been a problem for a while. Any ideas guys?

---

### Post by |{urse on 2010-03-07
anyone? bump.

---

### Post by pbrane on 2010-03-07
udev will assign the "ethx" value to each ethernet device it finds on boot with a different MAC address. I've not heard of this issue before. It's almost as if your MAC address is changing. Have a look at */etc/udev/rules.d/70-persistent-net.rules*. There should only be one entry for your wired ethernet device and (if you have one) one entry for your wireless device. Are you using wicd instead of NetworkManager? Maybe posting what desktop and version of ubuntu you are using would help.

---

### Post by dcstar on 2010-03-07
> **pbrane said:**
> 
........
Maybe posting what desktop and version of ubuntu you are using would help.

As well as whatever had been changed to the standard Ubuntu setup to cause the problem..... but I suspect that amount of detail may fill a screen.....

---

### Post by |{urse on 2010-03-08
Yeah I'm using Intrepid and I actually solved it. ACPI failure on the hardware end. I swapped boards and it's no longer a problem. =)

---

