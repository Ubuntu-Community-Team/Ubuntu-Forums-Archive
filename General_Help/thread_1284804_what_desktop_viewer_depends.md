---
title: "what desktop viewer depends?"
date: 2009-10-07
forum: General Help
---

### Post by abhilashm86 on 2009-10-07
when i use in built desktop viewer to access my friends computer in my LAN, its too slow, the frames are slow in loading and renderning, 

does this remote desktop viewing depends on internet speed? my spped is 2 Mbps, i get download speed upto 290 kbps,
 
is there any easy command line remote login system? i tried ssh, but many times ssh port is blocked, also we need to have account in that system?
any good alternate command line terminal remote login tools?

---

### Post by 3rdalbum on 2009-10-07
Yes, when you access SSH you need to specify a username that exists on the remote system, for example:

```
ssh username@192.168.0.12
```

The remote desktop shouldn't depend on internet connection speed unless the internet is between your computer and his/hers. Remote Desktop is fast enough on my LAN where I get data rates of around 20 megabits per second.

You might want to use X over SSH instead of VNC; it allows you to run graphical programs across a network, with the program's windows appearing on your display:

```
ssh -XC username@192.168.0.12
gnome-system-monitor
```

Enjoy.

---

### Post by abhilashm86 on 2009-10-07
> **3rdalbum said:**
> Yes, when you access SSH you need to specify a username that exists on the remote system, for example:

```
ssh username@192.168.0.12
```

The remote desktop shouldn't depend on internet connection speed unless the internet is between your computer and his/hers. Remote Desktop is fast enough on my LAN where I get data rates of around 20 megabits per second.

You might want to use X over SSH instead of VNC; it allows you to run graphical programs across a network, with the program's windows appearing on your display:

```
ssh -XC username@192.168.0.12
gnome-system-monitor
```

Enjoy.

hi its good to see you are enjoying 20MBps, my connection is just 2mbps, but i get max of 200kbps, thats remote desktop is really slow, i'l try X and reply back.........

---

