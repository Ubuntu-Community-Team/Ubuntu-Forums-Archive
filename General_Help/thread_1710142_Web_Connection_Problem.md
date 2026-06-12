---
title: "Web Connection Problem"
date: 2011-03-19
forum: General Help
---

### Post by ZJE123 on 2011-03-19
I currently own a dell XPS M1530 with an Intel 4965AGN Next-Gen Wireless-N Mini-Card  as the wireless card.  When I log into Ubuntu 10.10, I open up Google Chrome and most of the tabs load up.  Then I go to surf the web and none of the pages load and eventually, Google Chrome will just say that the page could not be loaded, and I can't use the internet at all because of this.  I am currently connected to a router that works because I can log onto my Windows partition and it works fine.  I am current using a WPA-Personal security type with a TKIP Encryption type.  What is the problem I am encountering?  Any help would be appreciated.

PS: I am using the 64-bit version of it.

---

### Post by grahammechanical on 2011-03-19
Can you confirm that Ubuntu is connecting to the router? Is there a network icon? Does it have a red exclamation mark against it? Do you get a message saying that you are connected to your wireless network? If you left click the icon can you see the your wireless network in the list?

The browser will load a lot of stuff from its Cache. The server not found message could mean 1) Ubuntu is not connected to the router. 2) the router is not connected to the ISP. 3) The web site address was wrong. Also think about this: Are you switching off the wireless adapter when you are using Windows? If so, this may prevent it from being switched back on when Ubuntu loads.

Regards.

---

### Post by falko on 2011-03-19
Do these commands work?

```
ping -c4 google.com
```

```
ping -c4 74.125.79.104
```If the second command works, but the first one doesn't, you probably have wrong nameservers in /etc/resolv.conf - try ```
nameserver 8.8.8.8
```

---

### Post by ZJE123 on 2011-03-19
> **grahammechanical said:**
> Can you confirm that Ubuntu is connecting to the router? Is there a network icon? Does it have a red exclamation mark against it? Do you get a message saying that you are connected to your wireless network? If you left click the icon can you see the your wireless network in the list?

The browser will load a lot of stuff from its Cache. The server not found message could mean 1) Ubuntu is not connected to the router. 2) the router is not connected to the ISP. 3) The web site address was wrong. Also think about this: Are you switching off the wireless adapter when you are using Windows? If so, this may prevent it from being switched back on when Ubuntu loads.

Regards.


According to Ubuntu, it is connected to the router the icon says that there is internet and according to Ubuntu, it is connected to the internet.  A pop up says that it's connected and the router IS in the drop down.  The router must be connected to an ISP because other computers are able to connect to it as well as my Windows partition, and my wireless adapter is always on(it is controlled by a switch on the outside of the laptop), and I doubt that every single webpage I've tried to load was down.

---

### Post by ZJE123 on 2011-03-19
> **falko said:**
> Do these commands work?

```
ping -c4 google.com
```

```
ping -c4 74.125.79.104
```If the second command works, but the first one doesn't, you probably have wrong nameservers in /etc/resolv.conf - try ```
nameserver 8.8.8.8
```

I'll give it a try, and let you know.

---

### Post by ZJE123 on 2011-03-23
> **falko said:**
> Do these commands work?

```
ping -c4 google.com
```

```
ping -c4 74.125.79.104
```If the second command works, but the first one doesn't, you probably have wrong nameservers in /etc/resolv.conf - try ```
nameserver 8.8.8.8
```

Nope, none of it worked, internet on it still doesn't work.

---

### Post by ZJE123 on 2011-03-23
> **grahammechanical said:**
> Can you confirm that Ubuntu is connecting to the router? Is there a network icon? Does it have a red exclamation mark against it? Do you get a message saying that you are connected to your wireless network? If you left click the icon can you see the your wireless network in the list?

The browser will load a lot of stuff from its Cache. The server not found message could mean 1) Ubuntu is not connected to the router. 2) the router is not connected to the ISP. 3) The web site address was wrong. Also think about this: Are you switching off the wireless adapter when you are using Windows? If so, this may prevent it from being switched back on when Ubuntu loads.

Regards.

Nope, nothing I have tried has worked.

---

