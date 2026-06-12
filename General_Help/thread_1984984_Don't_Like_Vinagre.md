---
title: "Don't Like Vinagre"
date: 2012-05-22
forum: General Help
---

### Post by ant2ne on 2012-05-22
As an rdp client, vinagre leaves a sour taste in my mouth. 

I do a lot of rdp work into windows servers from my linux workstation. But the current rdp client is really bad.

Vinagre isn't very configurable and lacks many of the features of tsclient or mstsc. I'd like to be able to adjust the connected desktop/screen size, and I'd like to be able to bring local resources (hard drive, printers, etc) up to the device I connect to. I know tsclient did support these features. Does vinagre support these features in a cryptic way?

What other rdp clients do we have these days?

---

### Post by Derek Karpinski on 2012-05-22
Remmina is installed by default on 12.04.  It has way more options than vinagre.

```
sudo apt-get update && sudo apt-get install remmina
```

---

### Post by QIII on 2012-05-22
VNC, by its technological nature, is slow and coarse grained.  There are some improvements you can do to improve it.  Still, it is resource intensive both on you machine and bandwidth use.

But if you want RDP-like performance, FreeNX or NOMACHINE NX (which I use) are virtually indistinguishable from RDP in terms of performance.

---

### Post by ant2ne on 2012-05-24
Thanks!! I love remmina!

---

