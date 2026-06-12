---
title: "Do I need a firewall?"
date: 2010-10-26
forum: General Help
---

### Post by AstroLlama on 2010-10-26
Hi all, I'm doing some light web development, I installed php5 and apache on my laptop and read that when running apache your computer is technically a server and is thus vulnerable to computer wankery.

I'm looking for advice on whether or not I should install a firewall or if I don't really need it. The work I'm doing is not a professional website, just a place for some experiments. All the info I found on the web was targeted to professional web-developers, not so much for amateurs like myself. What do you think?

---

### Post by scottuss on 2010-10-26
How do you connect to the Internet? If you connect via a router, you don't need a firewall. If you connect directly via modem or USB Dongle, you do need a firewall.

---

### Post by gandaran on 2010-10-26
> **scottuss said:**
> How do you connect to the Internet? If you connect via a router, you don't need a firewall. If you connect directly via modem or USB Dongle, you do need a firewall.
+1, ubuntu has a firewall but its not enabled by default, to enable it install a firewall gui, 'gufw' is a simple gui you can use to enable it, install from the ubuntu software center

---

### Post by Penguin Guy on 2010-10-26
Most routers have built-in, preconfigured firewalls. If you have one of these, you won't need to worry about firewalls.

If you do not have a firewall setup already, then you really do need to set one up. Linux has it's own firewall, IPTables, built-in at the kernel level, but it will need to be configured either through the command-line (see [FONT="Courier New"]man iptables[/FONT]) or through a graphical frontend such as [gufw]("apt:gufw") or [firestarter]("apt:firestarter").

---

### Post by HermanAB on 2010-10-26
Howdy,

Always use strong passwords for ALL user accounts, then you should be OK.

---

### Post by mcduck on 2010-10-26
The best solution would simply be to configure the Apache server to only respond to incoming connections from localhost, or local network addresses.

[https://help.ubuntu.com/community/ApacheMySQLPHP#Securing%20Apache]("https://help.ubuntu.com/community/ApacheMySQLPHP#Securing%20Apache")

A safely configured system doesn't need a firewall. :)

edit:
..of course if you are behind a router there's no need to do even that, the server won't be accessible from the Net unless you configure your router to forward the connections to it. Without port forwarding the server will only be available in the local network.

---

### Post by AstroLlama on 2010-10-26
> **mcduck said:**
> The best solution would simply be to configure the Apache server to only respond to incoming connections from localhost, or local network addresses.

[https://help.ubuntu.com/community/ApacheMySQLPHP#Securing%20Apache]("https://help.ubuntu.com/community/ApacheMySQLPHP#Securing%20Apache")

A safely configured system doesn't need a firewall. :)


Thanks for the quick replies, you've all answered my question, and I've even got lots of reading/research for the next few days about ports and firewalls. I think I will simply block access to all outside connections and only make it available through [http://localhost](http://localhost).

---

