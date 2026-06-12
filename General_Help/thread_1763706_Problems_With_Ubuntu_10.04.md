---
title: "Problems With Ubuntu 10.04"
date: 2011-05-20
forum: General Help
---

### Post by reagen on 2011-05-20
Hi, everyone.

So here's what happened. I recently bought a new Laptop that runs on Windows 7 Home Edition, and everything was OK. But then, I remember how annoying Windows can be sometimes, so I decided to switch to Ubuntu.

I burn the CD, run the install, and it all goes smoothly.

But when I run it for the first time, problem appears:

1.For some reason, Ubuntu doesn't connect me to the net.
       I got a perfectly working Broadband connection, my old computer (Which is also running 10.04) always detect connections automatically when I plug cables in, I don't know why this new thing doesn't?

2.Sound doesn't work.

Truth be told, I'm just a noob when it comes to technology and all. So I would appreciate it if you kind people would tell me how to fix all this, starting with the net problem!
I've never got this kind of problems before in Ubuntu, I dunno why I have it now, but I know there'll be a way out, it's just the way with Ubuntu....

So, please help.
Any suggestions is most appreciated, Thanks anyway!

REAGEN

---

### Post by emiller12345 on 2011-05-20
You could start by restarting the Network Manager, see if that doesn't resolve things...
```

sudo service network-manager stop && sudo service network-manager start

```

---

### Post by reagen on 2011-05-20
emiller12345,

That's fast, Thank You.

Tried it but still don't work...

---

### Post by emiller12345 on 2011-05-20
if see if you have an IP ADDR
```

ifconfig -a | grep "inet addr:" | grep -v "127.0.0.1"

```To see if you have any ARP entries
```

arp -van

```To see all of your routes
```

route -n

```To see your default gateway
```

route -n | grep "UG"

```
Check each of these, there should be something at each...

---

### Post by reagen on 2011-05-22
OK. I tried and this is what I got....

> **emiller12345 said:**
> if see if you have an IP ADDR
```

ifconfig -a | grep "inet addr:" | grep -v "127.0.0.1"

```To see if you have any ARP entries

Nothing....

```

arp -van

```To see all of your routes

Entries: 0 Skipped: 0 Found: 0

```

route -n

```To see your default gateway

Kernel IP routing table
Destination          Gateway              Genmask Flags          Metric Ref             Use Iface

```

route -n | grep "UG"

```Nothing....


Any ideas?

---

### Post by Linux_junkie on 2011-05-22
It sounds to me that your computer is so new Ubuntu does not have a driver for the network card / modem your using.  You never mentioned how your connecting to the net.

---

### Post by reagen on 2011-05-22
Wow, that can happen?

I'm using a Vaio C series VPCCB1AFJ

Unfortunately, I don't know how I connect to the net.
Got a modem, and the cables.

I plug it in, it's on....that's how it always works.

---

### Post by Linux_junkie on 2011-05-22
If its wireless network card you can always check in network manager that wireless connection is enabled. Or that the wi-fi card in laptop is active.  If these things don't work get name of network card and search net for a ubuntu/linux driver for it.

---

### Post by hawthornso23 on 2011-05-22
For a new laptop you might have better luck installing 11.04. It supports newer hardware better. Login into the ubuntu classic desktop if you want to avoid the bleeding edge (aka unity).

---

### Post by reagen on 2011-05-22
Will try to find out....

Any more advices or solutions is most welcome

---

### Post by reagen on 2011-05-22
Well, in the end I install Ubuntu 11.04, and now everything works perfect.

I guess I should've done it from the beginning!

In anyway, Thanks to all of you for taking the time to answer! Really appreciate it!

Thanks a lot, thank you! See you in the forums!

---

