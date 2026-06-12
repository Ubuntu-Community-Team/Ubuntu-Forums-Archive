---
title: "Where is &quot;make&quot; ?"
date: 2006-04-13
forum: General Help
---

### Post by jdief on 2006-04-13
I'm trying to install various linx apps, VMWare Server, and the Cisco VPN Client both need to use the "make" command. But the I can't find the "make" command. What's the deal?](*,)

---

### Post by akron on 2006-04-13
You probably want to install the 'make' package first?

---

### Post by taurus on 2006-04-13
Open a terminal and type
```

sudo apt-get install build-essential

```
That will install make, gcc, and other needed utilities to compile/build things.

---

### Post by aysiu on 2006-04-13
For Cisco VPN, you'll need *build-essential* and the Linux headers and kernel source. These can all be installed through Synaptic / apt-get

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by jdief on 2006-04-14
Thanks, the apt-get install command worked great!  :mrgreen:

---

