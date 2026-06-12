---
title: "kubuntu network settings -- KNetworkConf"
date: 2006-04-30
forum: General Help
---

### Post by greenwoodman on 2006-04-30
I just put kubuntu on my box, but the network settings wont give me root access for some reason. I click "administrator mode" and type my password, then a small window appears that says 'detecting your current platform' but it instantly disapears and I have the same screen that I began with and cant do anything.](*,)

---

### Post by j-strap2 on 2006-04-30
Have you updated your system? The initial release had bugs in KDE and network configuration. Much better when fully updated.

---

### Post by greenwoodman on 2006-05-01
I cant update if I cant connect to the internet...

or can I?

---

### Post by linuxa on 2006-05-01
If I'm not mistaken, the first entry in your source.list (/etc/apt/sources.list) should be your install cd. Which means you should be able to remove knetworkconf and do a reinstall with whatever package manager that you are using.

Alternately, you could when prompted for your password in Knetworkmanager, copy down the command string, and paste to a Konsole to execute. After setting up your network from there, you should be able to update.

---

### Post by songochain on 2006-05-01
Also u can configure your ethernet using ifconfig and dhclient to configure ip, subnet, gateway...

---

