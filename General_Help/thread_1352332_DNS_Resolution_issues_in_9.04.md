---
title: "DNS Resolution issues in 9.04"
date: 2009-12-11
forum: General Help
---

### Post by michaelvoss on 2009-12-11
I've been using Ubuntu for several months now and really like it and want it to work for me.

In the past several weeks, DNS resolution for me has become very slow....like 30 or more seconds slow.

I use both Chromium and Firefox (3.0) and I have done some searching and tried most of the suggestions out there including:

OpenDNS
GoogleDNS
Editing the connections to use the DNS servers for both OpenDNS and Google.
Etc.,

These solutions do not work.

I have a PC on the network and it flies.

This didn't seem to be an issue for me at first so maybe an update at some point added something that made it so.

Any help would be appreciated.

---

### Post by i.r.id10t on 2009-12-11
What is in /etc/resolv.conf ?

---

### Post by jbslaw on 2009-12-11
A couple of other suggestions:

Many dns lookup problems are related to ipv6. You can either upgrade your router and/or isp to accommodate ipv6 or blacklist ipv6 in /etc/modprobe.d/blacklist.conf.

Also, Firefox allows you to disable ipv6 by typing "about:config" in the address bar and, after entering the configuration screen, doing a search for "ipv6.". The rest is self-explanatory.

---

### Post by michaelvoss on 2009-12-11
Thanks for the replies. I figured it was related to ipv6 but was confused when OpenDNS wasn't working for me like others. I have used opendns for years.

I knew about the fix to Firefox and hadn't tried it yet...primarily because I really prefer to use Chromium.

I have to confess that I'm enough of a noob that I don't quite understand how to blacklist ipv6 in /etc/modprobe.d/blacklist.conf.

---

