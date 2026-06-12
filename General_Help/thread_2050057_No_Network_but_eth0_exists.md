---
title: "No Network but eth0 exists"
date: 2012-08-30
forum: General Help
---

### Post by Kissell on 2012-08-30
I did a fresh install from the Ubuntu 12.04 alternative CD.

During the install it was downloading files from the web.

After the install, everything looked great, but I have no network connectivity on that machine (on my laptop now).

I run "ifconfig -a" from the terminal, and it shows "eth0" exists, but it doesn't have any IPv4 information.

And of course, the network cable is plugged in and there is a blinky activity light on the port.

Any ideas on what I can do next to fix this?

---

### Post by sandyd on 2012-08-30
post output of
```

sudo dhclient -r
cat /etc/network/interfaces
```

---

### Post by Kissell on 2012-08-30
"dhclient -r" has no output

here are the uncommented lines from "cat /etc/network/interfaces" in order
> auto lo
iface lo inet loopback
auto eth0
iface eth0 inet6 auto


---

### Post by Kissell on 2012-08-30
hmmm

I deleted the last line, "iface eth0 inet6 auto"

So only this remains:
> auto lo
iface lo inet loopback
auto eth0


And now it works.

So v12.04 setup my wired network connection for ONLY IPv6 by default?  Cause that's what it looks like to me.

I just got rid of that line and let it do "auto eth0" and it works fine now.

Thanks!

---

