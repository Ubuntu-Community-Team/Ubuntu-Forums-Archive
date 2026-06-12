---
title: "How to set a proxy for navigate on Internet? (on Ubuntu 11.10 Oneiric Ocelot)"
date: 2011-12-08
forum: General Help
---

### Post by Bruno81 on 2011-12-08
Hi.

I'm new and I'd like to know how to set correctly a proxy for navigate in a secure way on Internet (I've think to some proxy that block some porn sites or gaming sites).
Tnx so much for the welcome and tnx so much for the answers.

Best regards.

---

### Post by lechien73 on 2011-12-08
Hello & welcome to the forums,

There are a few content filtering options available, but none - in my opinion - are particularly good or easy to set up.

Probably the best thing would be to use OpenDNS ([http://www.opendns.com/home-solutions/parental-controls/](http://www.opendns.com/home-solutions/parental-controls/)).

---

### Post by Bruno81 on 2011-12-09
Hi.

Sorry if I answer only now......

I've try to set the ubuntu proxy ....I've set "Proxy HTTP" in mode "Manual" and I've set the IP and the door (8080 in my situation)....I've also run sudo apt-get update but seems that there's an error when try to find the IP.... is correct the way that I've take or not? I've made some mistake or is correct how I've tried to set the proxy?

Tnx again for the answers!!!!!!

P.S.: Sorry but I'm new with Ubuntu and Linux.....

---

### Post by lechien73 on 2011-12-10
Ah...sorry, I misunderstood your question. You are saying that you *already* have a proxy, and you want apt-get to run through it?

Do you know what kind of proxy it is, and what kind of authentication it uses?

The general way to add a proxy for apt, is:

1. Open a terminal window.
2. Type:

```
gksu gedit /etc/apt/apt.conf
```

3. Add these 2 lines to the apt.conf file:

```
Acquire::http::Proxy "http://username:password@proxy-ip:port/";
Acquire::ftp::Proxy "http://username:password@proxy-ip:port/";

```

4. Save and exit.
5. Now try:

```
apt-get update
```

again :)

---

### Post by Bruno81 on 2011-12-11
Hi again and tnx so much,

I've found  a site that is hidemya**.com and I'd like to set the IP:Port of some IP that appear into the list,
I've tried with the procedure that you've write but don' seems to run.....
On site chisonoio.it the IP is the same that I still have.....
I don't need autentication.....
So....what can be the problem?
Tnx so much again for the help!!!!!!!!!

---

