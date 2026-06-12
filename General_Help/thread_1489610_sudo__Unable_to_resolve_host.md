---
title: "sudo:  Unable to resolve host"
date: 2010-05-21
forum: General Help
---

### Post by hankafyin on 2010-05-21
Hey forum,

I am having a problem with Ubuntu 10.04.  I was setting up network sharing with Samba.  Set up went fine, then I decided to change the hostname.

Following instructions I found on the web, I edited etc/samba/samba.conf to reflect my desired hostname.

Now I have to use superuser to run synaptic or update center.  I don't know what else I have "broken".

I would like to change my hostname, if I did it incorrectly for 10.04 please enlighten me.

I am a new user to Ubuntu/linux so be gentle.

---

### Post by hankafyin on 2010-05-21
Sorry to waste your time, I found my answer. the problem was I did edit etc/hostname, but did not edit etc/hosts.

I made the change to etc/hosts, and everything is peachy again.

---

### Post by WorMzy on 2010-05-21
You have to be superuser to run Synaptic anyway. I presume you meant Software Centre? :P

---

