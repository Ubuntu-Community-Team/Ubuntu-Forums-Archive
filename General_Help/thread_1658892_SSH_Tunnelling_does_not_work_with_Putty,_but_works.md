---
title: "SSH Tunnelling does not work with Putty, but works with standard ssh"
date: 2011-01-03
forum: General Help
---

### Post by drf_av on 2011-01-03
Hi,

Today I tried using PuTTY to set up a socks proxy on my local machine, a procedure I used to do when I was not using Ubuntu which used to work flawlessly and out of the box... however, apparently putty is not able to set up a port on my PC, but if I use ssh -Dport, everything works smoothly. Again, this used to work out of the box on other distros... any hints?

P.S.: This is the third problem I'm having with standard operations in Ubuntu: pinentry-qt4 does not work, the scanner needs manual setting to permissions, now this... isn't this distribution supposed to be user friendly? I'm resorting to the terminal more than I ever did.

---

### Post by Brandon Williams on 2011-01-05
When you say that this doesn't work, exactly what do you mean? If I close my ssh tunnel and enter the same settings into the putty GUI, putty correctly establishes a tunnel and the tunnel works just the way that my ssh tunnel did. If you give some more details about any errors being output by putty, the port number you're using, whether the port is actually being opened, etc., we'll have an easier time offering some help.

---

