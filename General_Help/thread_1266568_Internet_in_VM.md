---
title: "Internet in VM"
date: 2009-09-14
forum: General Help
---

### Post by HalfCrackedTech on 2009-09-14
Can I get the Net in a Virtual Machine?   If so can someone point me to some good literature on the matter.

---

### Post by abyrne on 2009-09-14
It depends on what your Guest OS is. And what VM version your using

---

### Post by HalfCrackedTech on 2009-09-14
well i am running ubuntu 9.04 trying to run windows XP in Sun virtualBox OSE

---

### Post by Chronon on 2009-09-14
I have been able to do it with Virtualbox and either Windows or Linux guests for quite some time.

---

### Post by HalfCrackedTech on 2009-09-14
LAN or WAN?

---

### Post by falconindy on 2009-09-14
VirtualBox borrows your network connection from the host for any guest OS you install. If it works on the host, you'll get the same result in the guest.

---

### Post by Chronon on 2009-09-14
I just use the default settings (NAT).  The guest machine is treated as if it's on its own subnet.  This topic may help: [http://ubuntuforums.org/showthread.php?t=546234](http://ubuntuforums.org/showthread.php?t=546234)

> If you are using NAT, VirtualBox provides it's own subnet and dhcp server for this, which is unrelated to your real network. You need to do bridging and create new interfaces, under "Host Interface" in order to join your real network.

---

