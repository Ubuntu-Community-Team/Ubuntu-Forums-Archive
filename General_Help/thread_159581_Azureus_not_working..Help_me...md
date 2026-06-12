---
title: "Azureus not working..Help me.."
date: 2006-04-13
forum: General Help
---

### Post by sands on 2006-04-13
I'm having internet thru an ethernet card with a static IP..
Firewall is firestarter..
During port testing in config wizard it says some NAT problem with port 6881..

---

### Post by tenn on 2006-04-13
Do you have port forwarding set up and the port  open in firestarter,
this link might help with port forwarding.

[http://azureus.aelitis.com/wiki/index.php/PortForwarding](http://azureus.aelitis.com/wiki/index.php/PortForwarding)

---

### Post by Quinthius on 2006-04-13
There seems to be a common problem where the default java gets switched from sun to gjc, which messes up Azureus, I guess because the network code is handled differently or something.

If you're sure your firewall and forwarding and all that is set up correctly and still can't get connected to anything in Azureus, give this a try:

```
$ sudo update-alternatives --config java
There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
 +    2        /usr/lib/jvm/java-gcj/bin/java
*     3        /usr/lib/j2re1.5-sun/bin/java

Press enter to keep the default[*], or type selection number:

```

Choose whichever one corresponds with Sun's java, and then restart Azureus if you already have it running.

This worked for me, anyway :)

---

### Post by sands on 2006-04-13
even bittornado is not working..
It says that could not connect to peer..

---

### Post by taurus on 2006-04-13
You need to go into firestarter and open that port up (or whatever other ports you want to open--listen)!  Otherwise, that port is blocked and you can't download anything because of that!

---

