---
title: "Administrating computers remotely, how do i?"
date: 2006-05-12
forum: General Help
---

### Post by Zeroangel on 2006-05-12
OK, here is my situation. I occassionally do tech support on a public access computer network, and I have two PC's on that network running Ubuntu Linux (and I am hoping to add more in the future). The problem is that I cannot physically go there very often to run updates on the machines, and I  do not trust the users with the administrator password.

These machines are connected to the internet through a LAN and Router, and I want the ability to run console commands and possibly access the desktop through it.

What do I need to do? And should I assign the ubuntu rigs with a static network IP, or can I let the DHCP server do its job?

---

### Post by 3x3cvt0r on 2006-05-13
[QUOTE=Zeroangel]OK, here is my situation. I occassionally do tech support on a public access computer network, and I have two PC's on that network running Ubuntu Linux (and I am hoping to add more in the future). The problem is that I cannot physically go there very often to run updates on the machines, and I  do not trust the users with the administrator password.

These machines are connected to the internet through a LAN and Router, and I want the ability to run console commands and possibly access the desktop through it.

What do I need to do? And should I assign the ubuntu rigs with a static network IP, or can I let the DHCP server do its job?[/QUOTE]

Well to simply access the console of each system you just need to load openssh server and ssh into the system from your console.  You can also try using the remote desktop feature of each station you want to access and just  use a VNC viewer to get to it.  

Please note that if you have a firewall or router between you and these computers you may need to open the appropriate ports so that you can get to the correct systems

---

