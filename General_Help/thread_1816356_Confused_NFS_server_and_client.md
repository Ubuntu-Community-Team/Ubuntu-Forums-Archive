---
title: "Confused: NFS server and client"
date: 2011-08-01
forum: General Help
---

### Post by dandeliondream on 2011-08-01
Hi,
 
I am using VMware player running Ubuntu10.04.
 
I have setup a NFS server machine and a client machine.
 
On my NFS server,
eth0   inet address:192.168.126.129
eth1 inet address: 192.168.255.129
 
On my client,
eth0 inet address:192.168.126.130
eth1 inet addess:192.168.255.128
 
My question is what is going on here?
Am I right to say, from the server machine, if I ping 192.168.126.130, I am calling the client machine?
 
NFS server ip address is 192.168.126.129?
 
and what about 192.168.255.129? and 192.168.255.128?

---

### Post by karlson on 2011-08-01
> **dandeliondream said:**
> Hi,
 
I am using VMware player running Ubuntu10.04.
 
I have setup a NFS server machine and a client machine.
 
On my NFS server,
eth0   inet address:192.168.126.129
eth1 inet address: 192.168.255.129
 
On my client,
eth0 inet address:192.168.126.130
eth1 inet addess:192.168.255.128


My question is why would you need to have 2 networks on the server and the client and why do you configure IP addresses on an internal segment in the inconsistent manner namely

server: 129 client 130
server: 129 client: 128
> 
 
My question is what is going on here?
Am I right to say, from the server machine, if I ping 192.168.126.130, I am calling the client machine?


Yes

>  
NFS server ip address is 192.168.126.129?


Ok.

> 
and what about 192.168.255.129? and 192.168.255.128?

What about those?  I am not sure what you are asking and what the issue is.

---

### Post by dandeliondream on 2011-08-02
Thanks for your reply.
 
I need to have both server and client on host-only networking.
 
I'm trying to create a volume (i mean a directory) in the server so that my client can shared this volume.
 
Please advise.
 
> **karlson said:**
> My question is why would you need to have 2 networks on the server and the client and why do you configure IP addresses on an internal segment in the inconsistent manner namely
 
server: 129 client 130
server: 129 client: 128
 
 
Yes
 
 
 
Ok.
 
 
 
What about those? I am not sure what you are asking and what the issue is.

---

