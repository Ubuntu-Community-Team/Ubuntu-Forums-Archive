---
title: "Ubuntu server setup (9.10 until 10.04 LTS is released)"
date: 2010-04-06
forum: General Help
---

### Post by grmihel2 on 2010-04-06
Hi dear Linux g33ks :)

I'm an nearly new educated computer science student, who think that this Linux envoiroment could be fun to learn something more about than just kernal and structure og the OS and differences from evolution through Unix to Linux and windows.

Today, the only server experience I got, is from Windows servers... But as you all know, the performance and cost of win servs ain't that nice. So I saw my cut to build my home server as a Linux server, now I just need a little "push" in the right direction through the Linux jungle :)

I have 1 physical server, thats running 6 virtual servers atm, and I want the new Linux setup to do the same ofc.

Virt_server1: Logging network traffic
Virt_server2: Mail server
Virt_server3: File server (Shared directory with Windows client enviroment/desktops)
Virt_server4: Web server including MySQL DB
Virt_server5: Buckup server
Virt_server6: Network monitoring (using a free license of PRTG today monitoring switches/routers/servers by the SNMP protocol, want equal software with graphs and alarms on linux if possible?)


All those are running through VMware on a Microsoft server, so what I request from some of you guys who are more experienced than me is:

- A list of programs that can do equal services
- Link to tuts and guides
- and maybe a little suggestion from your point of view


I'm fairly Linux newbie, but quiet quick learner and ofc I got some DOS experience. I'm planning to run it on Ubuntu 9.10 server edition (until 10.04 is getting released). And ofc I wish to be able to control it remotely from my windows desktop if possible (like I can do today).


Thnx for your kindness

Best regards :KS

---

### Post by dominiquec on 2010-04-06
VMWare also runs on Ubuntu, and there are other virtualization alternatives like KVM that might suit your needs.

As you seem fairly advanced in skills, I suggest you look into [https://help.ubuntu.com/9.10/serverguide/C/index.html](https://help.ubuntu.com/9.10/serverguide/C/index.html) for pointers on the apps.

Have fun! ;-)

---

### Post by Iowan on 2010-04-06
+1 [Server Guide]("https://help.ubuntu.com/9.10/serverguide/C/index.html")

---

