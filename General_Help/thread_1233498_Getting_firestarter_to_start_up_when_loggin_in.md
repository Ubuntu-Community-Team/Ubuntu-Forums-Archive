---
title: "Getting firestarter to start up when loggin in"
date: 2009-08-06
forum: General Help
---

### Post by robotichead on 2009-08-06
Hello, just a quick question.
Is it at all possible to get firestarter to automatically open up when ever i log in? And is it at all possible to for it to start up without asking me for a password each time?

Thank-you.
(i am using Ubuntu 9.04, 64 bit version)

---

### Post by Revolutionary101 on 2009-08-06
It automatically starts at boot up.

---

### Post by sasho_zl on 2009-08-06
First of all Firestarter is only a tool for configuring the real firewall - Netfilter. Once the Netfilter is configured you don't need to start firestarter anymore.
Second - firestarter is old and not supported software. It could be even dangerous because it is run with root privileges!
My advice to you is to install current firewall configurator like gufw.

---

