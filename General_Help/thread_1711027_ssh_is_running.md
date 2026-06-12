---
title: "ssh is running"
date: 2011-03-20
forum: General Help
---

### Post by t0s on 2011-03-20
hi im new,
ssh is running on port 22 ... i installed putty i few days ago so i guess thats the reason. 

Shouldn't start only when i run putty and not every time i open my pc ?what i have to do not to have it open and just start with putty ? or am i missing something?

[I]
nmap -PN 192.168.1.100

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-03-20 23:49 EET
Interesting ports on 192.168.1.100:
Not shown: 999 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
[/I]
Nmap done: 1 IP address (1 host up) scanned in 0.09 seconds

---

### Post by tordeu on 2011-03-20
I am not sure, I understand the problem, but:
The open port is from the SSH server. The server needs to be running, so that you can connect to the machine using SSH. Otherwise you would need to start the SSH server on the machine you want to connect to everytime you want to connect to it, which does not make much sense, because why use SSH, when you have to go to that machine to start the SSH server.

---

