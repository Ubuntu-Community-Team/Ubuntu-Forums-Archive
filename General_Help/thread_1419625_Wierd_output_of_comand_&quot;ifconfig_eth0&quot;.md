---
title: "Wierd output of comand: &quot;ifconfig eth0&quot;"
date: 2010-03-02
forum: General Help
---

### Post by 71GA on 2010-03-02
Hello i have a problem. I cant find anything except my mac address if i type "ifconfig eth0" in terminal. 

There is no gateway adress ip adress and netmask. This is wierd. How can i asssign those to a eth0?

---

### Post by howlingmadhowie on 2010-03-02
> **71GA said:**
> Hello i have a problem. I cant find anything except my mac address if i type "ifconfig eth0" in terminal. 

There is no gateway adress ip adress and netmask. This is wierd. How can i asssign those to a eth0?

if you want to assign these, you can do this manually by typing 
```

sudo route add default gw xxx.xxx.xxx.xxx

```
and
```

sudo ifconfig eth0 netmask xxx.xxx.xxx.xxx

```
but usually the values are supplied by the dhcp server on the network.

you can also assign the values graphically by right-clicking the network icon at the top-right of the screen and selecting "modify connections".

---

