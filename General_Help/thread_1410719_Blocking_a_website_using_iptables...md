---
title: "Blocking a website using iptables.."
date: 2010-02-19
forum: General Help
---

### Post by karthick87 on 2010-02-19
I have read that there is a way to block websites using iptables but being a begginer i dont find the way to do it..Can anyone help me?Thanks in advance..

---

### Post by ankspo71 on 2010-02-19
Hi,
Are you only wanting to block a few sites to and from your computer, or are you looking for a blacklist to block all bad addresses? I can give you a few links to help you get started, until someone else can help. I only have some experience with setting some firewall rules, and the only blacklist I ever use is in the torrent programs.

Here is information on DansGaurdian. I think it is supposed to be a web content filter and blacklist, instead of being only a blacklist. [https://help.ubuntu.com/community/DansGuardian](https://help.ubuntu.com/community/DansGuardian)
(it can be found in synaptic package manager)

Here is some information on iptables
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
(actually, you'll probably never need to use this page. Also, editing the iptables directly can do more harm than good sometimes)

Here is information on how to use UFW (the built in command line firewall in ubuntu)
[http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html](http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html)
[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)
(A nice GUI(interface) for UFW is "GUFW") can be found in synaptic or ubuntu software center.
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

Some info on parental control
[http://ubuntuforums.org/showthread.php?t=843510](http://ubuntuforums.org/showthread.php?t=843510)

Hope this helps.;)

---

### Post by karthick87 on 2010-02-24
How to see the version of my iptables package

---

### Post by 3rdalbum on 2010-02-24
> **getyourkarthick said:**
> How to see the version of my iptables package

```
iptables --version
```

---

