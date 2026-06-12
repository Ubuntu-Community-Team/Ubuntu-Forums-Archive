---
title: "Routing Services"
date: 2010-12-31
forum: General Help
---

### Post by Ocxic on 2010-12-31
I have a DUAL WAN setup, and what i want to do is set it up so that certain OUTBOUND connections are routed through it's own WAN. Here's my setup (i only use ssh as an example service):

eth1 - Internal Network
eth2 - WAN-1 
eth3 - WAN-2

I want (and have it working as such):

eth1 <--All services -->WAN-1

I want:
```

eth1 <---All Services--->WAN-1
           |<---OUTBOUND SSH -----> WAN-2    

```This way everything is routed through WAN-1 and ONLY OUTBOUND SSH is routed through WAN-2.
Any ideas on how to accomplish this???

---

### Post by NFN_NLN on 2010-12-31
> **Ocxic said:**
> 
I want (and have it working as such):

eth1 <--All services -->WAN-1

I want:
```

eth1 <---All Services--->WAN-1
           |<---SSH -----> WAN-2    

```

This way everything is routed through WAN-1 and ONLY SSH is routed through WAN-2.
Any ideas on how to accomplish this???

Each WAN must have a unique IP... if so:

[http://www.debianadmin.com/howto-bind-ssh-to-selected-ip-address.html](http://www.debianadmin.com/howto-bind-ssh-to-selected-ip-address.html)

---

### Post by Ocxic on 2010-12-31
Thats great for incoming connections NFN_NLN, but I need to route outgoing connections.

---

### Post by NFN_NLN on 2011-01-02
> **Ocxic said:**
> Thats great for incoming connections NFN_NLN, but I need to route outgoing connections.

I've never had to specify outbound connections.  It appears Linux automatically picks an interface that works (which is great for 99.99% of cases).  According to the article below it can be done, but those are changes to the program itself.

[http://stackoverflow.com/questions/172905/using-linux-how-to-specify-which-ethernet-interface-data-is-transmitted-on](http://stackoverflow.com/questions/172905/using-linux-how-to-specify-which-ethernet-interface-data-is-transmitted-on)

---

### Post by HermanAB on 2011-01-02
Howdy,

You need to read the Advanced Routing Howto on [http://tldp.org](http://tldp.org)

---

### Post by Ocxic on 2011-01-02
I have it fixed with this: [http://linux-ip.net/html/adv-multi-internet.html](http://linux-ip.net/html/adv-multi-internet.html)

---

