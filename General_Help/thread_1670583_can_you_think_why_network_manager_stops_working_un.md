---
title: "can you think why network manager stops working under heavy load?"
date: 2011-01-19
forum: General Help
---

### Post by JuicyCouture on 2011-01-19
this is with both network manager and WICD, a problem i've had since i got ubuntu - multiple wipes and reinstalls

the wifi is supported out of the box, the problem i've randomly run into since installing is, it will randomly stop detecting networks "no networks detected"

i've noticed over time as this as been happening, that it usually happens whenever there is a high load - multiple videos going on multiple tabs, videos queued up etc.

its never happened during regular browsing - theres always a lot going on when it happens, almost like it collapses.

the only way to fix this, is to quit the manager - shut off the computer (restarting doesnt work) and then it comes back after


such a strange problem

---

### Post by 3rdalbum on 2011-01-19
It's not the Network Manager software, it's the driver that controls the Wifi device.

Under heavy load, a bug in the driver might leave the device in a messy state that causes it to stop working. Restarting the computer doesn't help, because the device itself hasn't been turned off. Shutting down the computer works, because the device loses power and therefore gets brought back to normal when the computer gets turned on again.

What wifi device are you using?

---

### Post by 3rdalbum on 2011-01-19
(double-post)

---

### Post by JuicyCouture on 2011-01-19
> **3rdalbum said:**
> It's not the Network Manager software, it's the driver that controls the Wifi device.

Under heavy load, a bug in the driver might leave the device in a messy state that causes it to stop working. Restarting the computer doesn't help, because the device itself hasn't been turned off. Shutting down the computer works, because the device loses power and therefore gets brought back to normal when the computer gets turned on again.

What wifi device are you using?


atheros 5001

---

### Post by JuicyCouture on 2011-01-19
> **3rdalbum said:**
> It's not the Network Manager software, it's the driver that controls the Wifi device.

Under heavy load, a bug in the driver might leave the device in a messy state that causes it to stop working. Restarting the computer doesn't help, because the device itself hasn't been turned off. Shutting down the computer works, because the device loses power and therefore gets brought back to normal when the computer gets turned on again.

What wifi device are you using?


atheros 5001, on an acer aspire 5520

maybe theres a key combo i can push to shut off the wifi adapter and turn it back on

---

### Post by JuicyCouture on 2011-01-19
> **3rdalbum said:**
> It's not the Network Manager software, it's the driver that controls the Wifi device.

Under heavy load, a bug in the driver might leave the device in a messy state that causes it to stop working. Restarting the computer doesn't help, because the device itself hasn't been turned off. Shutting down the computer works, because the device loses power and therefore gets brought back to normal when the computer gets turned on again.

What wifi device are you using?



maybe theres a key combo i can push to shut off the wifi adapter and turn it back on 

AR5001 Wireless Network Adapter

maybe this will help

[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

---

### Post by JuicyCouture on 2011-01-19
> **3rdalbum said:**
> It's not the Network Manager software, it's the driver that controls the Wifi device.

Under heavy load, a bug in the driver might leave the device in a messy state that causes it to stop working. Restarting the computer doesn't help, because the device itself hasn't been turned off. Shutting down the computer works, because the device loses power and therefore gets brought back to normal when the computer gets turned on again.

What wifi device are you using?



maybe theres a key combo i can push to shut off the wifi adapter and turn it back on 

AR5001 Wireless Network Adapter

maybe this will help

[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

---

