---
title: "Multiple Issues May Be Related"
date: 2009-07-27
forum: General Help
---

### Post by dannymichel on 2009-07-27
i have no internet when i start ubuntu but when i do 'sudo /etc/init.d/NetworkManager start' i do. i looked in system>preferences>startup applications and network manager is there. might this be related to the fact that my sessions arent saving for some reason? so i tried ticking/toggling the check box that says 'remember running apps' and restarting and even with it ticked/toggled off it starts pidgin on startup and no other app. no matter what i do it remembers pidgin and no other app. any ideas?

---

### Post by dannymichel on 2009-08-03
please?

---

### Post by 4Orbs on 2009-08-03
Before you log in, select "Sessions" at the login screen and select "Gnome Session". Then login. Thereafter you should be able to just log in normally and the desktop should load properly.

---

### Post by TheForumTroll on 2009-08-03
What do you get from a 'ifconfig' when the net doesn't work?

---

### Post by dannymichel on 2009-08-04
> **4Orbs said:**
> Before you log in, select "Sessions" at the login screen and select "Gnome Session". Then login. Thereafter you should be able to just log in normally and the desktop should load properly.
thanks.
network still not working though
> **TheForumTroll said:**
> What do you get from a 'ifconfig' when the net doesn't work?```
danny@danny-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6219 (6.2 KB)  TX bytes:6219 (6.2 KB)

danny@danny-desktop:~$ 

```

---

### Post by TheForumTroll on 2009-08-05
I dont know what the problem is :confused:

Well, you could try and configure it manually instead and see if it helps. It would be something like this:

ALT+F2 and type/paste:
```
gksudo gedit /etc/network/interfaces
```

Then enter whatever you need to setup the interface. If you get a IP address from your ISP with DHCP configure it by adding this:
```

auto eth0
iface eth0 inet dhcp

```

You might have to change eth0 to something else if you have more than one networkcard. Like eth1.

Hope it helps.

---

### Post by dannymichel on 2009-08-09
> **TheForumTroll said:**
> I dont know what the problem is :confused:

Well, you could try and configure it manually instead and see if it helps. It would be something like this:

ALT+F2 and type/paste:
```
gksudo gedit /etc/network/interfaces
```

Then enter whatever you need to setup the interface. If you get a IP address from your ISP with DHCP configure it by adding this:
```

auto eth0
iface eth0 inet dhcp

```

You might have to change eth0 to something else if you have more than one networkcard. Like eth1.

Hope it helps.
thanks
> **4Orbs said:**
> Before you log in, select "Sessions" at the login screen and select "Gnome Session". Then login. Thereafter you should be able to just log in normally and the desktop should load properly.i was mistaken.
that didnt work. ubuntu still not remembering my apps and windows.
pidgin also wont remember what status i had on startup.

---

### Post by TheForumTroll on 2009-08-10
Did it solve your problem? Sorry I can't help you with the remember session problem. Tried a google search but didn't find anything related.

---

