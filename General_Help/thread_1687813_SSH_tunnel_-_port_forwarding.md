---
title: "SSH tunnel - port forwarding"
date: 2011-02-14
forum: General Help
---

### Post by al_mic on 2011-02-14
Hello,

I hope that there is someone that can help me do what I intend to do.

Short: I want to connect from my private network at home to my private network at work to a Windows server, using remote desktop.

I have a router at home. On WAN interface is a public IP, on the LAN interface I have a local network using IPs from 192.168.1.0/24
My wireless laptop is using 192.168.1.34

I have a Linux router at work with public IPs on eth0 and a firewall that makes DNAT for some servers in the local network (connected to eth1) including for a Windows server.
The local network on eth1 is 192.168.3.0/24
The Windows server is using 192.168.3.11

I want to make a ssh tunnel from my home laptop to the Linux router at work, and through this tunnel to be able to use rdesktop to connect to the Windows server by Remote Desktop.

Do you know what ssh command should I use? And then if I must use a special rdesktop command too?

I tried using :
ssh -L 9999:<router_public_ip>:3389 al_mic@<router_public_ip>

and then

rdesktop -a 16 -f 192.168.3.11

But it does not work.

Any ideas?


It is not a big thing, but it bothers me that I don't know...

Any help is appreciated.

Thank you.

---

### Post by hawkmage on 2011-02-14
Try something more like:
```
 ssh -L 9999:192.168.3.11:3389 al_mic@<router_public_ip>
```

Then from annother command line:
```
rdesktop -a 16 -f localhost:9999
```

What you will do with that ssh command is have the ssh client listen on port 9999 and direct any traffic to it to the address 192.168.3.11 port 3389 on the host you are sshing into.

---

### Post by al_mic on 2011-02-14
Makes sense what you are saying.
Thanks for the tip.

I tried this now but it does not work:

$ ssh -L 9999:192.168.3.11:3389 al_mic@<router_public_ip>

and from a different terminal:

$ rdesktop -a 16 -f 192.168.3.11:9999
Autoselected keyboard map en-us
ERROR: 192.168.3.11: unable to connect


Could it be because on the remote Linux router (the linux form work) I have a iptables firewall that denies any 3-way-handshake (syn packets) coming from eth0 to eth1 ?
I do allow syn from eth1 to eth1 or syn from eth1 to eth0.
I also allow some syn from eth0 to eth1, but only to a few known ports (like 80 for some servers, 22 for ssh for some source IP). In rest syn is Dropped.


What should I do?
Allow syn from some source (I don't like this) or .. make ssh tunnel act as if it is generating traffic from eth1 (does it generate traffic from eth0 ? I don't know)

---

### Post by hawkmage on 2011-02-14
SSH tunnels are not like VPN connections where you referance the IP/Name of the system on the other side of the connection.

Don't use "rdesktop -a 16 -f 192.168.3.11:9999" Your local system on the 192.168.10/24 network knows nothing about the 192.168.2.0/24 network and can not get to it.  

Try the command I gave you:
```
rdesktop -a 16 -f localhost:9999
```
or 
```
rdesktop -a 16 -f 192.168.1.34:9999
```

---

### Post by al_mic on 2011-02-14
Oh, yes. You are right!
I did not read carefully.

After 

$ ssh -L 9999:192.168.3.11:3389 al_mic@<router_public_ip>

I must do a rdesktop to localhost (here is where I was not careful)

$ rdesktop -a 16 -f localhost:9999


And it works!!!

Thank you very much!

---

### Post by hawkmage on 2011-02-14
No problem.  Using ssh tunnels can be counter intuitive.

---

