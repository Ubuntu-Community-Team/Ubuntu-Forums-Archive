---
title: "Install via apt or ubuntu software center problem"
date: 2012-02-27
forum: General Help
---

### Post by teriyaki-89 on 2012-02-27
Hi everybody i use Ubuntu 11.10 and now got 2 network interfaces eth0 - ethernet 
and eth1 wimax which i start manually.
I need to install some packages via apt-get install or ubuntu software center, but when i invoke them i can't install anything. In network proxies i use no proxy and can connect via browser. Also i have routing enabled

route add -net 0.0.0.0 netmask 0.0.0.0 dev eth1
route add -net 10.0.0.0 netmask 255.0.0.0 dev eth0

So is it an ubuntu bug or should i change my config. 
When i install something via ubuntu software center it wrties update cache and nothing else
help me please

---

### Post by wildmanne39 on 2012-02-27
Hi please post the errors you get when you run:
```
sudo apt-get update
```
Thanks

---

### Post by teriyaki-89 on 2012-02-27
preciate for help

i got this 
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release:

[B]i used this and signature worked
$ sudo apt-get clean
$ cd /var/lib/apt
$ sudo mv lists lists.old
$ sudo mkdir -p lists/partial
$ sudo apt-get clean[/B]

[here is the link]("http://www.hbyconsultancy.com/blog/ubuntu-howto-fix-repository-signature-verification-issues.html")

---

### Post by raja.genupula on 2012-02-27
Thats good news , please mark the thread as solved . 

Thank you .

---

### Post by wildmanne39 on 2012-02-28
I am glad to hear you fixed it sorry I did not get back to you sooner my internet has been acting up to night.

---

