---
title: "Bridge Connections in 9.04 (Weird Problem, Please help!)"
date: 2009-07-22
forum: General Help
---

### Post by intx on 2009-07-22
Okay, so I have kubuntu 9.04.

I've read a LOT of information on bridging connections and I've got it working, mostly.


Here's what's in my /etc/networking/interfaces file: 

```
auto lo
iface lo inet loopback

iface br0 inet dhcp
    bridge_ports all
```


I have my PC with an ethernet cord going out to the back of my xbox 360.

I can initiate the bridge via konsole with 

```
ifup br0
```

Upon doing that, I can turn on my Xbox 360 and sign into Xbox live and everything works.

Now, I have no internet access on my PC. Which sucks. 

Now it's weird, I've managed to get internet on my pc every time doing this trick, but it only works for a second then stops.

I do the following commands: 

```
sudo route add default gateway 192.168.0.1
then
sudo dhclient br0
```

As soon as I hit enter on the second command, my internet on my PC will work for about one to two seconds, then stop.


What can I do? I have a Windows 7 setup I use and it was a few clicks to get it working. I don't want to have to boot that every time I want to play xbox live.

(PS, got Kubuntu yesterday, still learning. Amazing OS though)

Can anyone help me?

---

### Post by intx on 2009-07-22
Anyone?

Still need help.

---

### Post by intx on 2009-07-22
bump.

---

### Post by intx on 2009-07-22
still need help.

---

### Post by intx on 2009-07-23
bump =/

---

