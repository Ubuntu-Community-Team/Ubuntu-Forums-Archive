---
title: "Ubuntu and Razer Naga"
date: 2012-08-13
forum: General Help
---

### Post by Equilibrium31 on 2012-08-13
Hello,

I've just recently started using Ubuntu and I'm wondering if there is any way to get my Razer Naga mouse to work with the OS.  Currently, the mouse does not function at all when connected.  I have searched to see if there are any available drivers or other methods, but have not found anything.  

I am aware that there are some issues with getting the buttons on the side of the Naga to work with Ubuntu, but if I can at least get it to work as a normal mouse for now, I will be satisfied.  Thanks.

---

### Post by ubudog on 2012-08-14
Hi Equilibrium31, could you plug in the mouse and then post the output of:
```
lsusb
```

Best,
ubudog

---

### Post by tsofras on 2012-08-19
Have exactly the same problem, i have to unplug and then pluging the mouse again in order to be recognised from ubuntu

this is the output from lusb
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c223 Logitech, Inc. G11/G15 Keyboard / USB Hub
Bus 007 Device 006: ID 1532:0015 Razer USA, Ltd 
Bus 007 Device 004: ID 046d:c221 Logitech, Inc. G11/G15 Keyboard / Keyboard
Bus 007 Device 005: ID 046d:c225 Logitech, Inc. G11/G15 Keyboard / G keys


```

---

