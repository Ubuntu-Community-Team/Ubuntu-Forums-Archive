---
title: "Is ubuntu safe out of the box?"
date: 2009-09-18
forum: General Help
---

### Post by FrankQC on 2009-09-18
Do I need to configure any iptables or any other firewall to make it safe or has it already been done for you?

---

### Post by ardchoille42 on 2009-09-18
> **FrankQC said:**
> Do I need to configure any iptables or any other firewall to make it safe or has it already been done for you?

As far as I know Ubuntu is safe in that 1) [Linux is safer]("http://ardchoille42.blogspot.com/2009/02/linux-and-viruses.html"), 2) there are no world-facing services in use.

For the firewall, though, you can install Firestarter (in the repos) and go through the setup wizard, it's extremely easy.

---

### Post by doas777 on 2009-09-18
short answer yes.

no system is "secure", and no system is completely "safe", but ubuntu is "Safe Enough" for most people straight out of box. there are no open network ports, sudo restricts admin to specific accounts, and there is little to no common malware that will run on ubuntu.

there are all kinds of shades of grey to this question, but for a standard user desktop with no net services and a savy user,  ubuntu is more than safe enough by default.

you only want to install/configure a firewall if you have remotely accessible net services on the box and want to open a port for it. otherwise you can just leave it as is, since you don;'t have any open ports.

that said be careful about enabling services unless you know how to lock them down. the "Remote Desktop" or samba sharing for instance should only ever be deployed behind a router or other firewalling device.

---

### Post by FrankQC on 2009-09-18
Awesome, thanks.

I've only been using Linux for a year so I still have to learn about specifics i.e. iptables and firewalls, but at least I don't have to worry anymore about not being safe.

---

### Post by warp99 on 2009-09-18
Ubuntu is safe out of the box, but I would set up a firewall anyway and use strong passwords. The reasoning is that with Linux you become a target by experienced hackers versus the script kiddies that plaque Windows users. Let me explain, an experienced hacker when he/she stumbles across your machine will say to themselves  "they're using Linux, something important must be on there" and proceed to hack on your machine. Now since there are fewer experienced hackers obviously your risk is much lower, but if this person sets their sights on you the potential for damage is higher if your machine is not secured properly.

---

### Post by doas777 on 2009-09-18
> **warp99 said:**
> Ubuntu is safe out of the box, but I would set up a firewall anyway and use strong passwords. The reasoning is that with Linux you become a target by experienced hackers versus the script kiddies that plaque Windows users. Let me explain, an experienced hacker when he/she stumbles across your machine will say to themselves  "they're using Linux, something important must be on there" and proceed to hack on your machine. Now since there are fewer experienced hackers obviously your risk is much lower, but if this person sets their sights on you the potential for damage is higher if your machine is not secured properly.

that is exactly the case that would get you hacked. spear-phishing and other specifically targeted attacks will get through eventually, though usually some social component is needed. if you are a savy user, you can usually block that vector with some common sense and a little research.

---

### Post by linux_tech on 2009-09-18
There are some good suggestions here 
[http://maketecheasier.com/9-things-you-need-to-doinstall-after-installing-ubuntu-904/2009/04/22](http://maketecheasier.com/9-things-you-need-to-doinstall-after-installing-ubuntu-904/2009/04/22)

---

