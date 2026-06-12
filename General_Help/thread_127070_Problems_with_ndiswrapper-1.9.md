---
title: "Problems with ndiswrapper-1.9"
date: 2006-02-08
forum: General Help
---

### Post by BlacKoffee on 2006-02-08
Hello,

I'm trying to get ndiswrapper installed on my system, but it's giving me grief. I have everything extracted just fine, but when I go to the source directory and tell it to "make distclean" or "make install" my terminal tells me "bash: make: command not found." Here's what I'm doing...

user@name:~$ cd ndiswrapper-1.9
user@name:~/ndiswrapper-1.9$ make distclean
bash: make: command not found
user@name:~/ndiswrapper-1.9$

What am I doing wrong? This is driving me crazy >_< I'm sure it's something simple, but I'm so new to Linux, I'm clueless.

K0ff33

---

### Post by kaamos on 2006-02-08
Try this:
```
sudo apt-get install build-essential
cd ndiswrapper-1.9
sudo make install

```
On the other hand, why do you need 1.9 ? Installing ndiswrapper (older version) from synaptic is a lot easier.

[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

---

### Post by BlacKoffee on 2006-02-08
I did what you said and just went through synaptic. Now ndiswrapper is telling me that the driver I'm trying to install (the driver from the list of accepted drivers) is invalid. 

Any other ideas?

Aaron

PS: The driver I'm using is for Belkin F5D7000 v2. I have the F5D7050 wLAN USB adapter, but the 7000 driver should work with it.

---

