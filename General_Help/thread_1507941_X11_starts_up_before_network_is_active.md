---
title: "X11 starts up before network is active"
date: 2010-06-12
forum: General Help
---

### Post by jonasg on 2010-06-12
I'm building a HTPC using the minimal ubuntu variant.

I've come pretty far, having X11 with Graphic support and Boxee running.

The system boots extremely fast (no tweaking everything is default). So fast boxee is up and running before there is networking. 
The fast boot time is great. But I'd rather have a network connection before boxee is started.
I could write a bash script that checks if there is a connection and then launch boxee accordingly. 
But I'd rather have a more system wide solution. Can you modify the init system so it does what I want it to do ?

---

### Post by dcstar on 2010-06-12
> **jonasg said:**
> I'm building a HTPC using the minimal ubuntu variant.

I've come pretty far, having X11 with Graphic support and Boxee running.

The system boots extremely fast (no tweaking everything is default). So fast boxee is up and running before there is networking. 
The fast boot time is great. But I'd rather have a network connection before boxee is started.
I could write a bash script that checks if there is a connection and then launch boxee accordingly. 
But I'd rather have a more system wide solution. Can you modify the init system so it does what I want it to do ?

Remove the Network Manager package and manually set up the /etc/network/interfaces file.

---

### Post by jonasg on 2010-06-13
I don't think I have the network manager package installed or even in use.

I've started from a minimal ubuntu variant. 

```

media@Hades:~$ sudo ps -ef  | grep -i network
media     1749  1506  0 14:39 pts/1    00:00:00 grep --color=auto -i network

```

The /etc/network/interfaces file looks ok:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

---

