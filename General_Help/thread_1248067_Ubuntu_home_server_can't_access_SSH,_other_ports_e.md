---
title: "Ubuntu home server: can't access SSH, other ports externally"
date: 2009-08-23
forum: General Help
---

### Post by CoreyWhite on 2009-08-23
Hello!

I am quite new to Ubuntu and Linux in general. I've run some Ubuntu desktop VMs in the past for testing purposes, and dual-booted Kubuntu for a while on an old laptop, but I never really dug into the internals; I just used it as a drop-in Windows replacement.

Now I'm trying something a little different. I recently bought a new laptop, and rather than throwing out my old one, I decided to hook it up to a 1.5TB external hard drive and use it as a home server. The plan is to use it primarily for file storage on my home network via a Samba share, but I also plan to set up media streaming (Jinzora or something), run a web server, and have a Linux PC to mess with remotely via SSH. This is more of a learning/hobbyist project, than anything, so I wanted a full-on Linux installation rather than something like FreeNas or Amahi.

I installed Ubuntu Server (9.04). That installation was very smooth, no problems. All is well on the laptop. Updated everything, no issues. It runs constantly, silently, and without much power consumption with the lid close -- I couldn't be happier with the idea of using an old laptop as a home server.

During the initial installation, I selected OpenSSH Server and pretty much nothing else, planning to build everything else up as I went. So far, so good, and I was able to SSH into it on the default port (22) from my new Mac laptop on the same server. Everything seems fine with SSH, and since getting that connected, I haven't done anything at all on the laptop itself -- everything has been done via SSH from my Macbook Pro or Putty from my Windows desktop PC.

Here's where I run into problems. I want to be able to access the new "server" via SSH from outside my home network. I have been tearing my hair out trying to get this to work, and simply haven't been able to.

My home network is based on a Netgear WGT624 V3 router connected to a cable modem. I have it set to reserve a specific local IP for the "server" via the LAN IP Setup menu: 192.168.1.10, not that that should matter.

The router has Dynamic DNS capabilities, and I set to use the DynDNS service; on DynDNS, I set up a hostname of coreywhite.homeip.net, and my router should now be automatically mapping its external IP address to that domain whenever my ISP changes it. This works fine, and I confirmed this by turning on my router's remote management option on port 8080. From outside my home network, I can now configure my router by visiting coreywhite.homeip.net:8080. (I'm doing it at the moment, in fact.)

I have also turned on Port Forwarding on the router to forward port 22 UDP/TCP to the server IP address, 192.168.1.10. I have rebooted both the router and the laptop/server, although I don't believe either should be necessary.

This just doesn't work . . . I have found references online to similar problems with other distros that are related to iptables settings, but Ubuntu evidently comes without any blocked ports. I can verify that SSH is open and listening, because it works when I'm on my home network . . . but SSH just times out when I try from outside my home network. Doesn't respond to ping at that port, either. I have tried changing the port to a couple of random numbers, 341 and 11111 (on the off-chance that my ISP is actually blocking port 22), with the same results: works internally, fails to work outside my network.

I'm at my wits' end. I don't even know whether the issue is with my Ubuntu installation or with my router. Is there something simple I'm overlooking? Some OpenSSH setting to block SSH connections from external IP addresses, for example?

I've tried Googling, and found a number of threads that seem relevant, but the threads either die away with no resolution, or the solution is something I've already checked. I'm quite new to all of this, but unfortunately this is one thing I have to get working before I can really work more. My plan is to administer this server remotely almost all of the time via SSH, during my downtimes at work. I would greatly appreciate any help. Thanks!

---

### Post by ghostmac on 2009-08-23
Your router isn't accepting incomming traffic on port 22. 
Are you sure your port forwarding is setup correctly?

---

### Post by CoreyWhite on 2009-08-23
Pretty sure. (I've set up port forwarding for other ports in the past without any issues.) Not *certain*, though. I guess the easiest way to check would be to install OpenSSH server on one of my other computers and then set up Port Forwarding to that, instead. I think it's easy to do on my Mac . . . I'll check when I get home.

Thanks!

---

### Post by CoreyWhite on 2009-08-24
Okay, I've ruled out problems with the port forwarding. Today, I switched the forwarding to the my Mac laptop instead and activated Remote Login (the built-in SSH server) in OS X. I just now verified from work that I am able to SSH to the DynDNS domain coreywhite.homeip.net, and that the SSH connection is being forwarded to my Mac laptop. Able to connect via Putty from work, browse around my Mac laptop, etc.

So it appears that both port forwarding and the DynDNS service are working fine -- the issue seems to be that my Ubuntu Server setup is not listening for SSH connections external to my home network.

---

### Post by CoreyWhite on 2009-08-24
Using a port scanning tool like [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/), I've found that any ports that I forward to my laptop running Ubuntu Server do not respond (in particular, I would expect 80 and 22 to respond), but when I forward the same ports to my Mac laptop, ports 80 and 22 show as open.

Is there any good reason that OpenSSH would not listen for connections forwarded from external IP addresses? It seems like it should be a simple setting somewhere, but I can't find anything. It's really boggling my mind.

---

### Post by CoreyWhite on 2009-08-26
Well, I don't know if this will help anyone else or not.

I couldn't figure out my issue, and eventually last night in desperation I just wiped the drive completely and reinstalled Ubuntu Server, and then reinstalled OpenSSH via Aptitude.

Today, I tried from work, and now I'm able to access the server perfectly fine via SSH. No issues at all.

I have no idea what caused the problem, but reinstalling Ubuntu fixed it.

---

