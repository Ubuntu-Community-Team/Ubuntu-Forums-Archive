---
title: "Update Manager not working after network change"
date: 2009-10-13
forum: General Help
---

### Post by akber on 2009-10-13
Whenever I switch from my school connection (which requires I enable a different custom proxy) to my home connection (which requires switching back to the default proxy), the update manager wont be able to get updates from the repositories. 
I have tried it through the terminal as well and I can't get it to work. I am not a very experienced user and have tried the basic stuff: 

```
sudo /etc/init.d/networking restart
```And i turned off the wireless and then turned it back on, and still nothing. I have to completely restart the system, which is a real pain in the *** if i just want to update the system.

---

### Post by akber on 2009-10-13
bump

---

### Post by wojox on 2009-10-13
Try:

```
sudo ifconfig eth0 down
```

shuts down the eth0 interface, releases the IP


```
sudo ifconfig eth0 up
```

enables the eth0 interface, renews the IP

---

### Post by akber on 2009-10-14
> **wojox said:**
> Try:

```
sudo ifconfig eth0 down
```shuts down the eth0 interface, releases the IP


```
sudo ifconfig eth0 up
```enables the eth0 interface, renews the IP

HMM. alright i will give it a try next time the problem occurs because for some reason it was working today. 

I'll let you know how it went, thanks

---

