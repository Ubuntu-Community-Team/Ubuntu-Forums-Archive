---
title: "Can't download using Synaptic"
date: 2010-01-06
forum: General Help
---

### Post by PDA1 on 2010-01-06
I can't download anything using Synaptic or the Ubuntu software center.  I'm trying to download Filezilla.

I can access the web and go to websites.

Gufw is not enabled and I've disabled iptables


Here's the error message I get with Synaptic;

W: Failed to fetch [http://archive.getdeb.net/ubuntu/pool/apps/f/filezilla/filezilla-common_3.3.0-1~getdeb1_all.deb](http://archive.getdeb.net/ubuntu/pool/apps/f/filezilla/filezilla-common_3.3.0-1~getdeb1_all.deb)
  404  Not Found

---

### Post by cpplinux on 2010-01-06
What does your /etc/apt/source.list look like? You can change the URL to [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) and have a try.

---

### Post by Kevbert on 2010-01-06
Comment out the line for [http://archive.getdeb.net/ubuntu/poo...etdeb1_all.deb](http://archive.getdeb.net/ubuntu/poo...etdeb1_all.deb) by adding # at the beginning of the line.
You should be able to get Filezilla via Synaptic Package Manager.

---

