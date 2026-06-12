---
title: "How do I edit /etc/network/interfaces file?"
date: 2006-04-01
forum: General Help
---

### Post by harisund on 2006-04-01
Ok, here is the setup

I have a wired connection at eth0 and the corresponding line in */etc/network/interfaces* is
```
inet eth0 iface dhcp
```

and for my eth1 wireless PCMCIA card it is 
```

inet eth1 iface dhcp
   wireless-mode managed
   wireless-key 12345.....
   wireless-essid FooBar

```

When it boots, it simply hangs at the *Configuring network interfaces* section until I abort it with a Ctrl C. I do this, and consequently my wireless card doesn't acquire an IP address either ;-(

The other interesting thing is, I tried commenting out my first line (the eth0 line) and when it booted up, my wireless had become eth0 !! So I changed the thing again, and it once again crashed on *Configuring network interfaces*.

So my question is, how do I use *iface eth0* to disable it, instead of asking it to search from DHCP??? Or do you think giving it a static IP might fix the problem?

---

### Post by hw-tph on 2006-04-01
There should be a line that says "auto eth0". Comment that out (or delete it) and the eth0 interface shouldn't be brought up automatically.

For reference, read interfaces(5) (**man 5 interfaces**) 

Håkan

---

### Post by harisund on 2006-04-01
ok ... thanks ! That seems to have taken off the eth1, just the way I had wanted !

---

