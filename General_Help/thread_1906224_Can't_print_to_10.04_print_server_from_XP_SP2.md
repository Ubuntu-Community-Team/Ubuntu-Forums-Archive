---
title: "Can't print to 10.04 print server from XP SP2"
date: 2012-01-08
forum: General Help
---

### Post by Mirrorboy on 2012-01-08
I set up a print server running Ubuntu 10.04 and the one XP SP2 machine in my house can't connect/print. It was working with no problem up until a few days ago when a power outage screwed up my printing system. So I reconfigured everything and now the XP machine won't connect. I really don't know what other details to include because I'm completely stumped. Any help is welcome.

---

### Post by bluexrider on 2012-01-08
generally its a permissions issue on the server side. check to make sure the windows machine is granted access and make sure the printer is shared

---

### Post by Mirrorboy on 2012-01-08
> **bluexrider said:**
> generally its a permissions issue on the server side. check to make sure the windows machine is granted access and make sure the printer is shared

The printer is being shared because all the other machines in question can connect. How do I check if the XP machine has permissions? I'm a complete Ubuntu noob. I mean, I love the OS and it's great if I just need to get up and go, but I'm completely useless when it comes to troubleshooting it.

---

### Post by bluexrider on 2012-01-08
> **Mirrorboy said:**
> The printer is being shared because all the other machines in question can connect. How do I check if the XP machine has permissions? I'm a complete Ubuntu noob. I mean, I love the OS and it's great if I just need to get up and go, but I'm completely useless when it comes to troubleshooting it.
here is a guide for print server setup [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by Mirrorboy on 2012-01-08
That really didn't help. I did everything in the server setup section and the information of what ports to have open are for IPP, not Samba. What else you got?

---

### Post by bluexrider on 2012-01-08
questions here? have you tried restarting the offending PC? If all the other machines are able to use the print server.....

do you have a network that you can 'view' each machine?

---

### Post by Mirrorboy on 2012-01-09
I've rebooted the machine in question, didn't do anything.

---

