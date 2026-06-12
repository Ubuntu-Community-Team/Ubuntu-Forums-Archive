---
title: "problem with internet connection"
date: 2012-01-16
forum: General Help
---

### Post by road kill on 2012-01-16
i have finished uninstaling vista and instalin ubuntu, and now i have some problems with my internet connection...

i dont know why but i cant seem to connect my emachines 525 with internet...

i went to System Settings and to Network and the choose Wireless... now im getting a warning: Firmware missing. 

What does this mean ? How do i fix it ?

---

### Post by gandaran on 2012-01-16
go to system settings » additional drivers to activate wireless drivers, if you have broadcom brand wireless chipset they need driver activation or installing from software center.

---

### Post by road kill on 2012-01-16
error: No proprietary drivers are in use on this system.

---

### Post by gandaran on 2012-01-16
you need to be connected with wired internet to get the wireless drivers
if you still have the problem post the output of his command
```
sudo lshw -C network
```

---

### Post by road kill on 2012-01-16
thanks for all your help :)

can you recomend the best driver for me ? how does  ipw2200 sounds ?

---

### Post by gandaran on 2012-01-16
> **road kill said:**
> thanks for all your help :)

can you recomend the best driver for me ? how does  ipw2200 sounds ?
if you have an Intel wireless chipset you don't need to install any driver as Intel drivers are already built in the kernel and wireless should be working, in the panel network icon does it detect any networks? (check if wireless networks are enabled)

please post the command output I asked for.

---

