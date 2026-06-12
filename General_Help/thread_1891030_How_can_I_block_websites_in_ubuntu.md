---
title: "How can I block websites in ubuntu?"
date: 2011-12-04
forum: General Help
---

### Post by sinaphysics on 2011-12-04
Hi,
I want to block websites in ubuntu, as i find in web I must use these
sudo gedit /etc/hosts 
and then adding 127.0.0.1 [www.facebook.com]("http://www.facebook.com") 
this work. but when I use proxies like TOR or YOURFREEDOM and like this, it doesn't work. what u suggest?

---

### Post by oldtimer7777 on 2011-12-04
> **sinaphysics said:**
> Hi,
I want to block websites in ubuntu, as i find in web I must use these
sudo gedit /etc/hosts 
and then adding 127.0.0.1 [www.facebook.com]("http://www.facebook.com") 
this work. but when I use proxies like TOR or YOURFREEDOM and like this, it doesn't work. what u suggest?

I use OpenDNS nameserver, and I block everything I want with a list on OpenDNS.  And I also use Moblock and Mobloquer.   You can easily install those from the moblock repositories.

---

### Post by collisionystm on 2011-12-04
I suggest you do not use a public proxy like TOR or YOURFREEDOM. Why would you even trust something like that? Just because its a proxy does not mean its not tracking your data. Only trust a proxy that you yourself personally made.

---

### Post by oldtimer7777 on 2011-12-04
> **collisionystm said:**
> I suggest you do not use a public proxy like TOR or YOURFREEDOM. Why would you even trust something like that? Just because its a proxy does not mean its not tracking your data. Only trust a proxy that you yourself personally made.

They are sitting at the other end of that Tor proxy listening to everything, and copying it.  It would be better to run your own private network with encryption that nobody knows about but you and keep changing it periodically.

---

### Post by sinaphysics on 2011-12-04
Thanks dears. But I live in Iran and there is a high barrier and filtering here which cause I use these proxies. and in addition I don't know how to make a proxy to pass Iran filtering.
and how can I manage openDNS? can u guide me? step by step !

---

### Post by oldtimer7777 on 2011-12-04
> **sinaphysics said:**
> Thanks dears. But I live in Iran and there is a high barrier and filtering here which cause I use these proxies. and in addition I don't know how to make a proxy to pass Iran filtering.
and how can I manage openDNS? can u guide me? step by step !

Try using Moblock first.. That should block whatever web sites you want locally.

---

### Post by sinaphysics on 2011-12-04
how can i install and config it?

---

### Post by uRock on 2011-12-04
> **sinaphysics said:**
> Thanks dears. But I live in Iran and there is a high barrier and filtering here which cause I use these proxies. and in addition I don't know how to make a proxy to pass Iran filtering.
and how can I manage openDNS? can u guide me? step by step !

Circumventing legal barriers is against our Code of Conduct.

Thread Closed.

---

