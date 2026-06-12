---
title: "cable internet just quit working"
date: 2010-06-22
forum: General Help
---

### Post by danbuter on 2010-06-22
I've been using my laptop a fair amount, plugged into cable. It quit working about 30 minutes ago, even though my Windows machine connects fine.

I am using a Lenovo Edge. I had just run the Hardware Drivers program just prior to the cable stopping working. Not sure if that would cause the issue or not. It worked fine up until then. 

I did not install any new updates today.

lspci gives
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

I have tried rebooting and resetting my router, neither of which worked.

---

### Post by Noz3001 on 2010-06-22
Have you checked ifconfig? Is your device up?

---

### Post by danbuter on 2010-06-22
Just ran it. It says UP LOOPBACK RUNNING.

---

### Post by CharlesA on 2010-06-22
Run this in a terminal and post the results.

```
ifconfig
```

---

### Post by Noz3001 on 2010-06-22
Try **sudo ifconfig eth0 up** in a terminal. If eth0 is your adaptor.

---

### Post by danbuter on 2010-06-22
Didn't work.

---

### Post by danbuter on 2010-06-22
The first ifconfig was for l0, it now has a result for eth0. Unfornately, neither will actually let me connect to anything, even though both say UP RUNNING.

eth0 says UP BROADCAST RUNNING MULTICAST MTU:1500 Metric: 1

---

### Post by danbuter on 2010-06-22
I checked the Network Connections program. I had to add a wired connection. Do I need some kind of MAC address for my home cable?

---

### Post by CharlesA on 2010-06-22
Sounds like you don't have an ip address.

Try running this:

```
sudo dhclient
```

---

### Post by danbuter on 2010-06-22
That did it! Thanks very much!

I have no idea how my ip address got lost, though.

---

### Post by CharlesA on 2010-06-22
The lease probably expired or something and it didn't want to refresh it.

Glad it's working now. :)

---

### Post by no2498 on 2010-06-23
that was odd
just seen this post as my other computer went off line it has 910 on it
so i was reading this and this 1 went off line it has 804 on it
wife was on her vista box playing games on line
until i had to reset the router
the 910 did say the lease expired
glad he got his working

---

### Post by danbuter on 2010-06-23
More weirdness. I had to use dhclient again today to get my connection to work again. Is there some way to make Ubuntu remember my IP address?

---

