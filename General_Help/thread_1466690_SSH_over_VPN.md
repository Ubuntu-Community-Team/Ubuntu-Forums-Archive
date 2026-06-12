---
title: "SSH over VPN"
date: 2010-04-30
forum: General Help
---

### Post by mail_e36 on 2010-04-30
Hello friends,

Let's assume I have established a** VPN tunnel using Vpnc from the an Ubuntu 9.04 machine to a Cisco PIX** (a VPN endpoint/router/firewall).  Once I am on the VPN, my remote **Ubuntu box **is assigned an internal IP address from the VPN pool.  Using this IP  address I have full access to other machines on my LAN (ping, telnet,  ssh, etc.) Everything seems normal.

The problem comes in when **I want to use another Linux machine (also ****Ubuntu)**** on my  internal LAN as my 'gateway' to the internet using "ssh -D" from the  VPN'd host **(the remote Ubuntu machine, in this case).  I make the "ssh -D" connection  from my VPN'd in remote Ubuntu machine to the LAN linux machine, but any attempts to  browse the web from the remote Ubuntu machine fail (I have set up the remote machine's Firefox  browser to listen using SOCKS on localhost (127.0.0.1) on a specific  port).  (I have even tried the  "Links" text-only CLI browser, using the proper  SOCKS configuration with no luck, so I know it's not a browser issue). 

I have also tried this entire setup using the **Cisco native VPN client**  on a Windows XP machine with the **same results** (I can ping, ssh,  telnet, etc, but 'ssh -D' doesn't do anything), so I know the problem is  not with the remote Ubuntu machine, per se.   

For background information, the "ssh -d" is supposed to specify a local  ''dynamic'' application-level port forwarding. This works by allocating a  socket to listen to port on the local side, bound to a specified bind  address. Whenever a connection is made to this port, the connection is  forwarded over the secure channel, and the application protocol is then  used to determine where to connect to from the remote machine.  In  essence, I am trying to create a tunnel using SSH to my linux box so I  can browse the web over the VPN.

Additionally, this entire **setup works perfectly when my remote Ubuntu machine is  sitting locally on the LAN** (bypassing the VPN altogether), so it  seems my "ssh -D" command is correct.  I am missing one crucial piece,  but I am not sure what this piece is.    

Considering the caliber of IT knowledgeable individuals on this forum,**  I am hoping someone can share their ideas.   **

Thank you

---

### Post by dino99 on 2010-04-30
can't answer you but wonder if you can have a good one on this general forum, better to post on network forum i guess

---

### Post by koanhead on 2010-04-30
I'm unclear on exactly what you are trying to accomplish, but it sounds as if the situation is rather more complex than it needs to be.
First, some things you probably already know: ssh does not require a VPN to work. It is an answer to some problems (for example, tunneling through a local firewall) but not necessarily the best answer. Using the -D switch for ssh makes little sense in this context, particularly combined with the use of a VPN.
Someone else might make more sense of this than I have to date. Would you be willing to re-state the problem, identifying which host runs sshd and which runs ssh (that is, which one you are connecting *to* and which you are connecting *from*.) I had a hard time figuring out which is which.
If all you are trying to do is specify an alternate (non-default) gateway for a web-browser to use, I feel sure there are easier ways ;^)

---

### Post by mail_e36 on 2010-04-30
[koanhead]("http://ubuntuforums.org/member.php?u=132241"), thank you for your quick response.  The goal of this effort is to access the internet through the VPN tunnel from a remote computer which connects to the VPN.  We'll call this remote computer Machine A.  I would like to browse the web from my remote machine (Machine A) by using a VPN as if I am on my home on my LAN.  On my home LAN I have another machine running, which we'll call Machine B, this machine is running SSHD (the SSH Daemon 'server').  The goal here is to connect to my LAN first, and access the internet through the LAN,  thereby not using an insecure free Wi-Fi internet connection on which Machine B sits which can be sniffed by hackers.  To clarify, the scenario is like this:

Machine A is the VPN remote client which runs the free VPNC (VPN Client) software.  

We are assuming I have established a** VPN tunnel using Vpnc (a free VPN client) from the the remote machine running Ubuntu 9.04 (which we'll call Machine A) to a Cisco PIX** (which is a VPN endpoint/router/firewall).   Once I am on the VPN, my remote **Ubuntu box (Machine A) **is assigned an  internal IP address from the VPN pool of IP addresses of the LAN which the VPN server (Cisco PIX) sits on.  Using this IP  address I have  full access from Machine A to other machines on my LAN (ping, telnet,  ssh, etc.), including full access to Machine B which runs SSHD and is to serve as my Internet Gateway.  Everything seems normal.  However, the problem is I cannot browse the internet directly using this VPN connection without using a Internet gateway (Machine B) sitting locally on my LAN which I have connected to via the VPN connection.  This is a limitation of the Cisco PIX device which I own, and is precisely why I need to use an Internet gateway (Machine B) to connect through to begin with.  I cannot access the internet directly from my VPN hosts.  

The problem comes in when **I want to use Machine B (a Linux machine running also ****Ubuntu) which sits****  on my  internal LAN as my 'gateway' to the internet).  In order to establish a connection to Machine B from Machine A I use "ssh -D" from Machine A** (the remote Ubuntu machine, in this case).  I make  the "ssh -D" connection  from my VPN'd in remote Ubuntu machine (Machine A) to the  LAN internet gateway linux machine (Machine B), but any attempts to  browse the web from the remote  Ubuntu machine (Machine A) fail (I have set up the remote machine's Firefox  browser  to listen using SOCKS on localhost (127.0.0.1) on a specific  port).   (I have even tried the  "Links" text-only CLI browser, using the proper   SOCKS configuration with no luck, so I know it's not a browser issue). 

I have also tried this entire setup using the **Cisco native VPN client**   on a Windows XP machine with the **same results** (I can ping, ssh,   telnet, etc, but 'ssh -D' doesn't do anything), so I know the problem  is  not with the remote Ubuntu machine, per se, but rather with my entire setup.   

Additionally, this entire **setup works perfectly when my remote Ubuntu  machine (Machine A) is  sitting locally on the LAN** (bypassing the VPN  altogether, on the same LAN as Machine B), so it  seems my "ssh -D" command which I run on Machine A is correct since it can talk to Machine B (by using "ssh -D") when locally on the same LAN (bypassing the VPN).  I am missing  one crucial piece here,  but I am not sure what this piece is.    

Please advise, I would very much appreciate it.  

Thank you in advance.

> **koanhead said:**
> I'm unclear on exactly what you are trying to accomplish, but it sounds as if the situation is rather more complex than it needs to be.
First, some things you probably already know: ssh does not require a VPN to work. It is an answer to some problems (for example, tunneling through a local firewall) but not necessarily the best answer. Using the -D switch for ssh makes little sense in this context, particularly combined with the use of a VPN.
Someone else might make more sense of this than I have to date. Would you be willing to re-state the problem, identifying which host runs sshd and which runs ssh (that is, which one you are connecting *to* and which you are connecting *from*.) I had a hard time figuring out which is which.
If all you are trying to do is specify an alternate (non-default) gateway for a web-browser to use, I feel sure there are easier ways ;^)

---

### Post by koanhead on 2010-05-01
According to the ssh man page, "Only root can forward privileged ports."
I don't know which port(s) you have set up the SOCKS proxy to use, but, for example, trying to use Firefox as the local (unprivileged) user would result in a failure to connect to port 80 (for example) if I am reading this correctly.
Also, the combination of ssh -D and VPN tunneling could be problematic. I'm pretty sure that the VPN tunnel is not needed for a remote machine (connecting via the internet) to an internet gateway on your network. It's already encrypted via ssh, so I don't see any advantage to using the VPN connection, unless your router requires it. I do see a possible opportunity for port/socket contention there.

---

