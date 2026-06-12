---
title: "TFTP server cannot bind to NIC"
date: 2009-07-17
forum: General Help
---

### Post by bwitherell on 2009-07-17
Hello,

Im am very stumped on this one. Hopefully someone can help.

I am running Ubuntu 9.04 (Jaunty). It seems like no matter what TFTP server I intall every time i try to start a TFTP server it does not bind the NIC or NICs ip address. I always get some variant of this message: 0.0.0.0 Port 69, bind failed, Address already in use. What is the deal? I don't get it. Why can't it listen on my IP? BTY 0.0.0.0 for this TFTP server means all/any interfaces/IPs on the PC.

any help would be appreciated.

Thank you :confused

---

### Post by t4thfavor on 2009-07-17
Looks like your already running one, lookup netstat, and ps to see how to discover what process is bound to that port.

---

### Post by bwitherell on 2009-07-17
> **t4thfavor said:**
> Looks like your already running one, lookup netstat, and ps to see how to discover what process is bound to that port.

Yea.... you're right I think what happened was that I botched the config for the server so it ran and never closed. I used ps to see the running processes but it didnt show it running. HAHAHA but the funny thing is that i did ps -a not ps -e lol. OOOOPPPPSSS. I can't believe i did that. Anyway i just rebooted and now it works :oops: Sorry id10t Error.

Thank you so much for the help.

BTW if you are looking for a good tftp server check this out. Has windows and linux version no compile/install required.
[http://sourceforge.net/projects/tftp-server/]("http://sourceforge.net/projects/tftp-server/") very quick and easy config, good documentation and open source.

---

### Post by t4thfavor on 2009-07-17
I tend to use the tftp-hpa server, as it has a nice setup, and tends to work nicely for all of my tftp'ing needs.

---

