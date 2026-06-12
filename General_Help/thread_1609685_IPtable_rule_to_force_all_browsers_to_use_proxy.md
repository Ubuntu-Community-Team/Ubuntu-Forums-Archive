---
title: "IPtable rule to force all browsers to use proxy"
date: 2010-10-30
forum: General Help
---

### Post by karthick87 on 2010-10-30
I have installed squid as my proxy server in ubuntu 10.04 standalone system..Why i have installed squid in standalone sytem is, my friends used to  access my system to browse sites and download files..So i have installed squid to block porn sites and downloads..But they simply bypass the proxy by disabling it..I know there is some way to force all browsers to go through proxy using iptables..But how to acheive it..?

Is the below command suits my need..?If not what modification should i do..?

```
[COLOR=red]sudo iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-port 3128[/COLOR]
```

---

### Post by karthick87 on 2010-10-31
Any recommended suggestion?

---

### Post by karthick87 on 2010-11-01
Bump.......>>>

---

### Post by karthick87 on 2010-11-01
Tried manythings but no use..Can some one guide me..?

---

### Post by blueridgedog on 2010-11-01
This covers it well:

[http://tldp.org/HOWTO/TransparentProxy-6.html](http://tldp.org/HOWTO/TransparentProxy-6.html)

---

### Post by karthick87 on 2010-11-01
> **blueridgedog said:**
> This covers it well:

[http://tldp.org/HOWTO/TransparentProxy-6.html](http://tldp.org/HOWTO/TransparentProxy-6.html)

Hey i am configuring it in standalone system man..Those configuration wont work here..

---

### Post by blueridgedog on 2010-11-01
Then just use the port argument:
```

iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128
```

This assumes eth0 is your inside interface...

This is a good link:

[http://www.faqs.org/docs/Linux-mini/TransparentProxy.html#s5](http://www.faqs.org/docs/Linux-mini/TransparentProxy.html#s5)

You can google on "iptables transparent proxy" if you want more good links.

---

