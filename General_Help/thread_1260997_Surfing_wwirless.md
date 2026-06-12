---
title: "Surfing w/wirless"
date: 2009-09-08
forum: General Help
---

### Post by Commander_Keen on 2009-09-08
So I am using a Dell Inspiron Laptop 1100 with a Linksys Router and a Netgear USB card.
This laptop is dual boot with XP and Ubuntu 9.04
If I leave a certain part of the house I can not surf the web with Ubuntu.  the Signal is fine and If I use Windows XP it work's great.
  I have tried uninstalling and Installing the USB device.
  I have tried a netgear router.
  I have tried the Live Cd as well.  All with the same result.


Any idea of what I can do?

---

### Post by P4man on 2009-09-08
can you post the specific model of wlan stick?
To obtain that, open a terminal and type:

```
lsusb
```

post the results here.

---

### Post by Commander_Keen on 2009-09-08
> **P4man said:**
> can you post the specific model of wlan stick?
To obtain that, open a terminal and type:

```
lsusb
```

post the results here.

I'll do that when I get home.
but its the Netgear WG111v3

---

### Post by Commander_Keen on 2009-09-08
> **P4man said:**
> can you post the specific model of wlan stick?
To obtain that, open a terminal and type:

```
lsusb
```

post the results here.

Here is the result as you requested

jrothschild@ubuntu:~$ lsusb
Bus 001 Device 002: ID 0846:4260 NetGear, Inc. WG111v3 802.11g Adapter [realtek RTL8187B]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jrothschild@ubuntu:~$

---

### Post by P4man on 2009-09-09
Did some googling on that, and you could try this in a terminal:

```
sudo apt-get install linux-backports-modules-jaunty
```

(then reboot)

---

### Post by Commander_Keen on 2009-09-10
So I wanted to let you know that I tried it last night and it seemed to have worked.  
  So what was it, I did?
  what was broken?
  how did you know that would fix it?

Thanks again.

---

### Post by P4man on 2009-09-10
What it did was install newer drivers that are meant to come with the next kernel (and/or version of ubuntu), but "ported back" to the current kernels for jaunty. 

As for how I knew? I didn't, but I read somewhere someone with a similar issue got it solved in Karmic (the next upcoming ubuntu version), so I figured it was worth a shot. You now have  some of the kernel modules (drivers) that will ship with karmic.

---

### Post by Commander_Keen on 2009-09-10
that was very cool
  Thank you again.

---

