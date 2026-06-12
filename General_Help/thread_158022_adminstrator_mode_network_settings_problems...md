---
title: "adminstrator mode network settings problems.."
date: 2006-04-10
forum: General Help
---

### Post by larafan on 2006-04-10
sir,i was using ubuntu.now i just wanted to try kubuntu.when i go to the network settings under system settings.it says click adminstrator mode.where is this button?i see a eth0 interface......but i cant change anything there.plz anyone help

---

### Post by larafan on 2006-04-10
anyone please help me out.ebry 15 mins i am logging into windows just to see that anyone replied.is there any konsole/command prompt way of setting up your network in kubuntu with ip address,dns and subnet mask.please.

---

### Post by aysiu on 2006-04-10
Forget systemsettings. It's garbage.

Press Alt-F2. A dialogue box will pop up. In that box, type ```
kdesu kcontrol
```

Enter your password.

You're now in administrator mode.

---

### Post by larafan on 2006-04-10
thanx sir,the network config interface is not like ubuntu(gnome) here.i'll give my net details.plz tell me how to configure my connection

ip address:192.168.1.1
subnet mask:255.255.255.0
ip gateway:192.168.1.1
dns:61.1.96.71/69

whenever i enter dns its says "enter an alias first"...what is this
and there r so many addresses like 127.0.0.1,ipv5,ipv6.....plz help me in this step.

---

### Post by larafan on 2006-04-11
please....will anyone help me

---

### Post by FlakJacket on 2006-04-12
Is your network set on DHCP?  Do you have an eth1 ethernet card?  I found that it worked after enableing dhcp on the ethernet card and enabeling eth1 before enabeling eth0. I don't know about the alias though...

Hope that helps,
Flak

---

