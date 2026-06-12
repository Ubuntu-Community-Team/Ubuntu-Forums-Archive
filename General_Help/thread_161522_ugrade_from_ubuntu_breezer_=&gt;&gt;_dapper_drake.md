---
title: "ugrade from ubuntu breezer =&gt;&gt; dapper drake"
date: 2006-04-17
forum: General Help
---

### Post by paulus4605 on 2006-04-17
Dears
I have a question 
I've installed breezer like I want to, and now I want to do an upgrade towards dapper drake flight 6 does this means that i have to re configure for instance my wireless network again or is the configuration integrated in the dapper drake? thanks for your coop and feedbacK

Paul

---

### Post by mscman on 2006-04-17
If you only upgrade via dist-upgrade and you don't do a fresh install, then you should be able to keep your existing settings, although sometimes the names of your network interfaces can get changed during dist-upgrades (at least in my experience...)

---

### Post by paulus4605 on 2006-04-17
Does this mean that you might use the network settings you correctly configured with ndiswrapper? my networkdriver is a bcm43xx and I know by experience that it's a lot of work to get this driver to work ?

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=paulus4605]Does this mean that you might use the network settings you correctly configured with ndiswrapper? my networkdriver is a bcm43xx and I know by experience that it's a lot of work to get this driver to work ?[/QUOTE]
It doesn't require too much work. I needed to use ndiswrapper just like in breezy, and then blacklist the bcm43xx module from loading. Then I added ndiswrapper to the modules list. If you compile the new 2.6.16.5 kernel from kernel.org it provides better "out of the box support. Please note that your system may break with Dapper between now and the offical release on June 1st.

---

### Post by elsupermang on 2006-04-17
One of the things that I think most windows-> linux users don't get used to doing is creating seperate partitions for your folders. As a desktop user I create a seperate partition for /boot and /home and another one just for / (root, everything else). That way if you want to do a clean clean install of a linux distro while keeping your settings (firefox,documents,etc) but not your applications and everything else you can do that. And also if you corrupt your data partitions somehow your computer will still boot to windows or whatever else since /boot is it's own partition

---

