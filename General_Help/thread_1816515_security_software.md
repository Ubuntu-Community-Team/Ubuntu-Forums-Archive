---
title: "security software"
date: 2011-08-02
forum: General Help
---

### Post by shauno501 on 2011-08-02
im a complete newbie to ubuntu, they say linux is safe, is there any software i need ,to make it safer......

---

### Post by 3rdalbum on 2011-08-02
> **shauno501 said:**
> im a complete newbie to ubuntu, they say linux is safe, is there any software i need ,to make it safer......

Short answer: No.

Long answer: There's no software that makes Linux safer than it already is, really, but you should refrain from running internet-facing services that you don't absolutely need. For instance, if you don't need a web server, don't install one on your computer.

Enjoy Ubuntu.

---

### Post by Wim Sturkenboom on 2011-08-02
In general the advise is to 'install' a firewall. However a firewall is already installed (called iptables) and you only need a front-end for ease of configuration.

You can search synaptic for ufw (possibly already installed and install it if not done yet) and for gufw (graphical version).

---

### Post by Nytram on 2011-08-02
If you use Firefox I'd recommend the add-on NoScript, like the name implies it blocks scripts on untrusted sites, making your browser more secure.

---

### Post by 3rdalbum on 2011-08-02
I believe NoScript blocks scripts on any sites that you haven't explicitly allowed; that's probably the one piece of software that would help against malicious scripts. It's not too likely that you'll come across this sort of attack, and when you do usually the attack tries to run Windows code on your system (which, of course, doesn't work on Linux).

As for a firewall, I don't bother. When I'm on my home network I'm already protected by the firewall inside my modem/router and there's no security advantage to two firewalls, unless you don't trust the fabric of your own network - and if you don't, you have bigger problems.

Even for people who are not already firewalled, such as mobile broadband users or people who use open wifi, they don't need to bother with a firewall. Ubuntu, by default, doesn't have any open ports by default; so a firewall will not add to your security there unless you run things that open ports and listen to incoming connections.

---

### Post by haqking on 2011-08-02
not good to post multiple threads

[http://ubuntuforums.org/showthread.php?t=1816513](http://ubuntuforums.org/showthread.php?t=1816513)

---

