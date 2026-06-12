---
title: "ssh problems (multiple computers with the same IP)"
date: 2010-12-17
forum: General Help
---

### Post by laus_deo on 2010-12-17
So I'm trying to ssh into my laptop through putty from my home's desktop so that I can transfer over some files and I can't find my flashdrive, but there are several windows laptops in my house, which have the same ip address, so when I try to access my ip it says that the connection is refused. I've downloaded the ssh thing on my computer, and have ssh'd it  from other machines before, just never at home. Does anybody know what to do?

---

### Post by efflandt on 2010-12-17
How are multiple laptops on your home LAN ending up with the same IP address?  That should never happen if they automatically get private IP's from a broadband router.  Are you manually assigning multiple computers the same private IP.

You are not trying to ssh to it through your public IP or dynamic DNS name with port forwarding are you?  Most routers do not do loopback (LAN2LAN via public IP).  If that is the case you need to ssh to the LAN IP of the computer with the ssh server, not your public name or IP.

---

### Post by laus_deo on 2010-12-20
Okay, I found out what was happening. I usually go to a website, whatsmyip.org to find my IP address, and that registered them as having the same IP. I was confused as that usually works, but I found out how to find my IP address on the computer itself and that worked. Thank though. :)

---

### Post by djeikyb on 2010-12-21
Just FYI, the ip address you see at whatismyip.com is your public ip address assigned to you by your ISP. Every other device on your Local Area Network gets its own local ip address, which is what they use to talk to each other.

---

