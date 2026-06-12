---
title: "firewalls"
date: 2010-05-05
forum: General Help
---

### Post by Mr Nemo on 2010-05-05
Is a firewall necessary on ubuntu? I've never thought about it until now. Do I need one? If so whats a good firewall to install? As you can tell im not too knowledgeable on this subject. I know (i think) linux has a built in firewall called iptables but ive never used it or looked into it.

---

### Post by dino99 on 2010-05-05
you might install ufw and gufw (look at synaptic to find them)

---

### Post by Mr Nemo on 2010-05-05
ok I installed them and gave it a look. It said my firewall was not enabled (I enabled it). Does that mean I haven't had a firewall running at all?

---

### Post by dino99 on 2010-05-05
> **Mr Nemo said:**
> ok I installed them and gave it a look. It said my firewall was not enabled (I enabled it). Does that mean I haven't had a firewall running at all?

you need to activate it (enabled)

here is a outdated help about ufw, now you have nothing to tweak else than acivated it with its built-in default rules.

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

here is something more professional:

[http://1000umbrellas.com/2010/04/29/how-to-set-up-the-firewall-using-ufw-on-ubuntu-lucid-lynx-server](http://1000umbrellas.com/2010/04/29/how-to-set-up-the-firewall-using-ufw-on-ubuntu-lucid-lynx-server)

[http://www.linuxsecurity.com/content/section/9/161/](http://www.linuxsecurity.com/content/section/9/161/)

---

### Post by Mr Nemo on 2010-05-05
Thanks dino, you've been a great help.

---

### Post by XCan on 2010-05-05
By default, firewalls are not necessary in Ubuntu as none of your running processes are listening to the outside world. However, as you start to install server-apps, you may in some cases want a firewall.

---

### Post by robvas on 2010-05-05
> **XCan said:**
> By default, firewalls are not necessary in Ubuntu as none of your running processes are listening to the outside world. However, as you start to install server-apps, you may in some cases want a firewall.

You should still use one.

Are you behind a router or cable/DSL modem that uses NAT? That is a form of a firewall. (IE, do you have a private IP address (10.0.0.x, or 192.168.x.y)

---

### Post by Calash on 2010-05-05
I like running Firestarter more for the extra information it gives than anything else.

---

### Post by bodhi.zazen on 2010-05-05
> **Mr Nemo said:**
> Is a firewall necessary on ubuntu? I've never thought about it until now. Do I need one? If so whats a good firewall to install? As you can tell im not too knowledgeable on this subject. I know (i think) linux has a built in firewall called iptables but ive never used it or looked into it.

IMO, a better question is what do you want a firewall for ?

Ubuntu is not windows and there are no open ports by default. In addition, many people are using a router, and most routers have built in firewalls ...

So adding (enabling) a firewall on an Ubuntu Desktop is not particularly necessary and does no add to your security.

What is it you wish to allow / deny ?

See :

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by bodhi.zazen on 2010-05-05
> **Calash said:**
> I like running Firestarter more for the extra information it gives than anything else.

Running firestarter in that way is a (small) security risk as it runs as root. If you wish to monitor your network traffic watch your logs or use wireshark or snort.

If you use wireshark, DO NOT run it as root.

---

