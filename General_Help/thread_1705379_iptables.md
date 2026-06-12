---
title: "iptables"
date: 2011-03-12
forum: General Help
---

### Post by Achilles124 on 2011-03-12
I find Ubuntu very easy to use but one thing still baffles me: iptables.

Does someone know a tutorial that is still readable for someone who is not very knowledgable as I still am?

---

### Post by kidsodateless on 2011-03-12
have you tried googling it?

---

### Post by WorMzy on 2011-03-12
I used this: [https://wiki.archlinux.org/index.php/Simple_stateful_firewall](https://wiki.archlinux.org/index.php/Simple_stateful_firewall)

Skip the installation instructions, obviously. And any reference to /etc/rc.d/iptables should be modified to /etc/**init.d**/iptables (I think) for Ubuntu.

Oh, and commands that start with "#" meant they're being run as root. Use
```
sudo -i
``` to get a root shell for the duration of the tutorial, and don't include the "#" in the actual commands.

---

### Post by Lars Noodén on 2011-03-12
The one I used was the [Frozentux Iptables-tutorial](http://www.frozentux.net/documents/iptables-tutorial/).

---

### Post by YesWeCan on 2011-03-12
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables)

---

### Post by Achilles124 on 2011-03-13
thanks for your replies.:D

---

