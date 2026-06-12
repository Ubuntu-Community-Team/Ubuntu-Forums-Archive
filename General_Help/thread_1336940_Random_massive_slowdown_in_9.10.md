---
title: "Random massive slowdown in 9.10"
date: 2009-11-25
forum: General Help
---

### Post by hydrogen18 on 2009-11-25
My setup is as follows:
Core i7 CPU
4gb DDR3 RAM
Asus p7p55d le motherboard
Seagate 1 TB drive
4x Seagate 1.5 TB drive in RAID10 with mdadm
1x WD 200 GB drive
Radeon HD 2400 XT

I have ubuntu 9.10 installed. The main purpose of this server is ssh server, openvpn server, NFS server, apache2 server, proftpd server, hosting a Windows 2003 Server VM, hosting a Debian Lenny Server VM, and playing video on its X session.

The system occasionally has its reponsiveness go to nearly infinity. This persists for up to 20 minutes the resolves itself, then reappears again after some random amount of time. No use of the server is possible. The VMs are almost totally unresponsive, ssh is extremely high latency, NFS serves files at a very low rate. The X session essentially becomes unusable.

During these periods of unresponsive behavior, the values reported from uptime go up to values between 14 and 16. Normally these are somewhere between 1 and 3. Hard drive access during this period is nearly 100%, the LED on the front of the machine which is connected to the motherboards HDD LED output stays on nearly the entire time. CPU usage reported by top is never more than 20-25% for all processes totalled.

Ubuntu 9.10 is installed to the seagate 1 TB drive. Content is stored on the RAID 10 array. VMs exclusively use the WD 200 gb drive.

What could possibly be the cause of this anomaly?

---

### Post by jacobs444 on 2009-11-25
sounds like you're overloading it with all the vm's and such. Honestly i have no Idea. are you using tue hardware raid?, if not then the raid is probably the problem.

---

