---
title: "firestarter problem, the firewall"
date: 2009-07-26
forum: General Help
---

### Post by Arminius on 2009-07-26
hey, whenever I boot up, it comes up with "nope you can't auto load firestarter u need root privileges" so I have to click on it, punch in the password.

can I tell the OP "no firestarter doesn't need root privileges?"
or any other solution?

---

### Post by lovinglinux on 2009-07-26
You don't need to run Firestarter at boot. Once you configure the firewall rules you can and should close it for good.

Firestarter is just a firewall-manager, that allows you to create the rules for the real firewall (iptables). This means the firewall is loaded at boot and runs in the background, even when Firestarter is not running.

Firestarter is not recommended anymore. You should try [gufw](apt:gufw) [apt-get] 

BTW, you can't run it without root privileges.

> [color=#CC0000]**Note:**[/color] when you see [apt-get] after a link on my posts it means that you just need to click it to install the software. This is basically an easy way to perform an installation from the [repositories](http://en.wikipedia.org/wiki/Software_repository)  without running the command on a terminal. This is the same as running the command *sudo apt-get install* followed by the name of the program.

---

