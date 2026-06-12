---
title: "iptables redirect"
date: 2011-10-27
forum: General Help
---

### Post by Pooch on 2011-10-27
hello,

I am trying to add a rule to my iptables that redirects any outbound requests to [http://websiteA.com/](http://websiteA.com/) to [http://websiteB.com/](http://websiteB.com/). I am new to iptables and any solutions / steps in the right direction would be helpful. 

I am attempting to follow the iptables --help but am stumbling over the usage. ](*,)

As always, any advice is appreciated.
thanks.

---

### Post by 11jmb on 2011-10-27
That doesn't really sound like what iptables was meant for. Check out dnsmasq instead.

---

### Post by Pooch on 2011-10-27
thanks for the quick response 11jmb. dnsmasq got the job done.

i have another question though. is it possible to redirect a one url to another, not just hostnames? i don't think this can be done with dnsmasq

example: redirect [http://websiteA/](http://websiteA/) to [http://websiteB/myindex.html?id=1](http://websiteB/myindex.html?id=1)

---

### Post by 11jmb on 2011-10-27
Not sure, I haven't tried that. 

perhaps try pinging [http://websiteB/myindex.html?id=1](http://websiteB/myindex.html?id=1) and see if that has a static IP? then you could still use dnsmasq for the same purpose

---

