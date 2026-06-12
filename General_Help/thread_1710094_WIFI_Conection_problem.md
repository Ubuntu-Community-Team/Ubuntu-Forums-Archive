---
title: "WIFI Conection problem"
date: 2011-03-19
forum: General Help
---

### Post by lynxmann on 2011-03-19
[FONT=Times New Roman][SIZE=2]Hello,[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]I am new to Ubuntu, And downloaded the Ubuntu Netbook OS and it works great but I have a Hp mini 1010nr with built in wifi. I can not get Ubuntu to recognise it and so my Computer will not find my router network. How do I get it to get online? [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT] 
[http://www.netbooklaptopreviews.com/netbook-reviews/hp-mini-1010nr/](http://www.netbooklaptopreviews.com/netbook-reviews/hp-mini-1010nr/)

---

### Post by blueridgedog on 2011-03-19
I have a similar issue with a MacPro laptop.  After installation, I have to connect it to a wired Ethernet connection, then go to System > Administration > Hardware Drivers to get it to download the driver for the wifi chipset.  it may work for you.

If that fails, post the output of the following when run in a terminal:

```
lspci
```

---

