---
title: "Network detect prob"
date: 2011-10-03
forum: General Help
---

### Post by 3dmatrix on 2011-10-03
I face a strange network problem. If I restart my computer my network is well detected but if I keep my laptop on standby then on 'waking up' the laptop cannot detect network most of the time. So I have to again restart the computer. Is there anyway, I could force Ubuntu to re-detect / refresh my network detection.

.

---

### Post by dcstar on 2011-10-04
> **3dmatrix said:**
> I face a strange network problem. If I restart my computer my network is well detected but if I keep my laptop on standby then on 'waking up' the laptop cannot detect network most of the time. So I have to again restart the computer. **Is there anyway, I could force Ubuntu to re-detect / refresh my network detection**.


Yes, 10 seconds typing "ubuntu network restart" into Google will give you may things to read.

---

### Post by 3dmatrix on 2011-10-04
If I have to look for solution abt Ubuntu why foolishly search on google. Why not here. Anyway, anyone with a better reply. I need to know why is such a problem occuring. Just typing a code 10 times in a day (after every time i suspend the comp) is not a sensible solution. That is what a labour would do.

---

### Post by 3dmatrix on 2011-10-05
I tried all the following commands but non of them work :

sudo restart network-manager
sudo ifdown eth0
sudo ifup eth0
sudo networking restart
sudo restart networkmanager
sudo restart network-manager
sudo /etc/init.d/networking restart
sudo /etc/dbus-1/event.d/25NetworkManager restart

I still have to restart the computer every time I suspend the comp.

---

### Post by 3dmatrix on 2011-10-22
Should I consider there is no solution to this problem ?
Or is it a bug in Ubuntu ?

.

---

