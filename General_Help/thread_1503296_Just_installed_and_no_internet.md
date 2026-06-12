---
title: "Just installed and no internet"
date: 2010-06-06
forum: General Help
---

### Post by hermish on 2010-06-06
I just put a brand new hard drive in my computer and installed ubuntu for the first time. Everything seems fine with it, but i can't seem to get the internet to work. I am plugging in straight from the modem and it is working fine on another computer. I can't even get it to show up in ubuntu. Any ideas on what i am missing?
Thanks

---

### Post by Autodave on 2010-06-06
> **hermish said:**
> I just put a brand new hard drive in my computer and installed ubuntu for the first time. Everything seems fine with it, but i can't seem to get the internet to work. I am plugging in straight from the modem and it is working fine on another computer. I can't even get it to show up in ubuntu. Any ideas on what i am missing?
Thanks

Go to SYTEM > PREFERENCES > NETWORK CONNECTIONS.  On the WIRED tab, there should be a listing there such as WIRED AUTO eth0.  If not, click on ADD and follow the directions to see if it can install itself.

---

### Post by hermish on 2010-06-06
It doesn't pop up by itself in the wired tab like it should. I have tried adding it myself, but I still can't seem to get it to work. That's why I was wondering if i am missing something.

---

### Post by konsta82 on 2010-06-06
enter in terminal
```
sudo dhclient eth0
```
if you connect after this command,do all possible updates and restart. in some cases this can help

---

### Post by hermish on 2010-06-06
> **konsta82 said:**
> enter in terminal
```
sudo dhclient eth0
```
if you connect after this command,do all possible updates and restart. in some cases this can help

I tried this command. I got eth0: error while getting interface flag: no such device

any idea what that means?

---

### Post by konsta82 on 2010-06-06
check hardware drivers in system/admin
is there something about your networking device ?

---

### Post by Iowan on 2010-06-06
From a terminal (Applications>Accessories>Terminal) **sudo lshw -C network** should show more information about your netowrk devices.

---

### Post by hermish on 2010-06-07
> **Iowan said:**
> From a terminal (Applications>Accessories>Terminal) **sudo lshw -C network** should show more information about your netowrk devices.

I tried this and it told me "network unclaimed"
Then description was ethernet controller, and then all the details about it.
Still no internet when i plug it in though.

---

### Post by _khAttAm_ on 2010-06-07
Please give out more information on the type of internet connection. Also, post the output of ```
sudo lshw
```.

---

### Post by hermish on 2010-06-07
> **Iowan said:**
> From a terminal (Applications>Accessories>Terminal) **sudo lshw -C network** should show more information about your netowrk devices.

br@br-desktop:~$ sudo lshw -C network
[sudo] password for brandon:
  *-network UNCLAIMED     
       description: Ethernet controller
       product: N10/ICH 7 Family LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=56 mingnt=8
       resources: memory:efbfd000-efbfdfff ioport:ccc0(size=64)

---

### Post by hermish on 2010-06-07
> **_khAttAm_ said:**
> Please give out more information on the type of internet connection. Also, post the output of ```
sudo lshw
```.

what do you want to know from lshw? it output 9 pages of text, and i dont need to post it all right here.

---

### Post by _khAttAm_ on 2010-06-08
This:
```
sudo lshw | grep logical
```

---

