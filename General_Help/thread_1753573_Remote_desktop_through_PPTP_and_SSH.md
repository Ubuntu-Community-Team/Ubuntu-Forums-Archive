---
title: "Remote desktop through PPTP and SSH"
date: 2011-05-09
forum: General Help
---

### Post by IanWilson on 2011-05-09
(Please let me know if there is a more appropriate sub forum for this post)

I have to do some work on an Ubuntu 7.10 based workstation that is within a clients network (meaning I have limited ability to change network settings and I would rather not have to ask if possible). I am using OSX to connect. The client has given the the following access:

1. PPTP VPN access to their network
2. SSH access through the VPN to the Ubuntu workstation
3. Generally unlimited access to the workstation OS
4. Client is on a different continent so I cannot physically access the machine

I need to see a GUI desktop however, so I need to run a virtual desktop.

Q. Is it possible to run a virtual desktop under these constraints, if so could you point me to help / tutorials?

Thanks.

---

### Post by Azdour on 2011-05-09
Hi,

Do users use this machine and you want to see their desktop (e.g. remote support) or do you just want to access a desktop GUI for ease of use?

I have used the latter via VPN and SSH. I do this from Ubuntu (local) to Ubuntu (remote). I have never done this via OSX.

Are you able to install software on this machine?

I have installed vnc4server on the remote computer because I cannot be sure if anyone has logged in. The problem with the built-in remote desktop with Ubuntu is that it requires someone to be logged in.

With vnc4server I can ssh in as the user I want, launch vnc4server and then connect to it via VNC. How usable the desktop GUI over VNC is depends on the speed of your connection. I have some connections that are painfully slow and I usually end up purely using the SSH connection to the machine to do my work.

Others may be able to give you better alternatives.

---

### Post by IanWilson on 2011-05-09
There will not be users viewing the machine, I need the GUI for ease of use.

I am wondering if there will be a problem with the port VNC requires (5900?) will the network administrator need to open this or is this not important?

---

### Post by Azdour on 2011-05-09
Hi,

Thats true, if they are blocking that port it will need to be opened. I would also look at ssh port-forwarding if you have not already. VNC over VPN is not secure: 

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

