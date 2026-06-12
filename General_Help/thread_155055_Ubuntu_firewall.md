---
title: "Ubuntu firewall"
date: 2006-04-04
forum: General Help
---

### Post by nal on 2006-04-04
I just installed ubuntu on a computer that I will ssh into.  At the moment it will not allow me to.  What do I need to do for it to allow me to.  And how do I access the firewall.

---

### Post by NewbieNik on 2006-04-04
I believe you will need to install firestarter to access firewall configuration in a nice graphical interface (Or try configuring iptables by text editor...don't ask me how though)
This will allow you to open port 22 for ssh traffic. Try to restrict the address's you allow access from for greater security.

---

### Post by Darkriser on 2006-04-04
yes, firestarter adds you ability to maintain iptables (firewall) in an easy way. if you like some more challenging way, you can always use iptables command (type man iptables in console) even without firestarter.
(however, firestarter adds some more features like dynamic firewalling, etc.)

---

### Post by nal on 2006-04-04
thanks guys I knew I was forgetting something :)  Thats why I love ubuntu, if ya ever have a prob ask on the forums and you get it fixed asap :)

---

