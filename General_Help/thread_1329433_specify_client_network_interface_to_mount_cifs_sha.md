---
title: "specify client network interface to mount cifs share"
date: 2009-11-17
forum: General Help
---

### Post by mansonthomas on 2009-11-17
Hi,

 I've a server that has two network interface eth0 and eth1 and need to mount a filesystem with CIFS on a remote server.

On client :
 eth0 is used for http
 eth1 is used for samba mount.
 

I've set some rules on the server in firewall and samba config to allow only the ip of eth1 of the client.


How can I eplicitely force the client machine to use its eth1 network interface for the samba mount ? 


On many command, you can specify the network interface...

however, in man mount.cifs, I can find any relevant option to put it in the fstab.

Thomas.

---

### Post by mansonthomas on 2009-11-18
I've talked with some colleague and one told be that it would be possible with iptable to create a route that forces the traffic that goes to a particular ip on some specific port to use eth1 instead of eth0.

Any idea of how to write such rules ? 

I don't know iptable at all (I use ufw for the firewall, it's simple and fill my needs ;)

Thomas.

---

### Post by dcstar on 2009-11-18
> **mansonthomas said:**
> Hi,

 I've a server that has two network interface eth0 and eth1 and need to mount a filesystem with CIFS on a remote server.

On client :
 eth0 is used for http
 eth1 is used for samba mount.
 

I've set some rules on the server in firewall and samba config to allow only the ip of eth1 of the client.


How can I eplicitely force the client machine to use its eth1 network interface for the samba mount ? 


On many command, you can specify the network interface...

however, in man mount.cifs, I can find any relevant option to put it in the fstab.

Thomas.

Put the two interfaces on different subnets, set up manual routes to the remote range and the mount will use whatever interface you have configured to access that remote IP address.

---

### Post by mansonthomas on 2009-11-19
I can't do that, IP addresses are attributed by the hosting company and can't be changed.

---

### Post by mansonthomas on 2009-11-19
in fact, the two ethernet interfaces are on different subnet, so I'll try that.

---

### Post by slakkie on 2009-11-19
man route

---

### Post by mansonthomas on 2009-11-19
>man route

a post that add absolute no value to this thread...

---

### Post by slakkie on 2009-11-20
> **mansonthomas said:**
> >man route

a post that add absolute no value to this thread...

So you didn't execute the command, so you didn't see how to create static routes...

---

### Post by mansonthomas on 2009-11-24
like I said... no value added...

man whatever you want, google whatever you want is not a usable answer...

---

