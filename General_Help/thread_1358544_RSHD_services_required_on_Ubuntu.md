---
title: "RSHD services required on Ubuntu"
date: 2009-12-18
forum: General Help
---

### Post by mojo_man on 2009-12-18
Hello,

I have a very old Solaris 2.6 box which has files I have to transfer off of its hard drive. The only command I can see to be of use is rcp. 
I am running Ubuntu 9.04. Can someone tell me step by step methods to allow for a rcp transfer from my solaris box to my ubuntu box?

Right now when I try the RCP command to my ubuntu box is says connection refused.

---

### Post by lykwydchykyn on 2009-12-18
"connection refused" usually means that the port in question isn't open -- either it's firewalled or the rsh service isn't running.

Are you sure rshd is running on the solaris box?  Maybe it's not running on the standard port; try scanning the box with nmap to see what ports are open.

EDIT: nm, I reread your post; I thought you were trying to talk to an rsh daemon on the solaris box.  Have you installed rsh-server on the ubuntu box?

---

### Post by Cheesemill on 2009-12-18
If you already have or can get SSH on the Solaris box then you can use scp from the Ubuntu machine. For example:
```
scp user@solarisIP:/path/to/files /home/username
```

---

### Post by mojo_man on 2009-12-18
> **Cheesemill said:**
> If you already have or can get SSH on the Solaris box then you can use scp from the Ubuntu machine. For example:
```
scp user@solarisIP:/path/to/files /home/username
```

Hi,

You are right rshd is not runn on the solaris box but I do not think it has to be...rshd has to be installed on the ubuntu box since I am sending files to the ubuntu box. How do I set it up?

PORT      STATE SERVICE
7/tcp     open  echo
9/tcp     open  discard
13/tcp    open  daytime
19/tcp    open  chargen
21/tcp    open  ftp
23/tcp    open  telnet
25/tcp    open  smtp
37/tcp    open  time
79/tcp    open  finger
80/tcp    open  http
109/tcp   open  pop2
110/tcp   open  pop3
111/tcp   open  rpcbind
139/tcp   open  netbios-ssn
143/tcp   open  imap
443/tcp   open  https
512/tcp   open  exec
513/tcp   open  login
514/tcp   open  shell
515/tcp   open  printer
540/tcp   open  uucp
764/tcp   open  omserv
1103/tcp  open  xaudio
2049/tcp  open  nfs
4045/tcp  open  lockd
6112/tcp  open  dtspc
7100/tcp  open  font-service
8082/tcp  open  blackice-alerts
32771/tcp open  sometimes-rpc5
32772/tcp open  sometimes-rpc7
32773/tcp open  sometimes-rpc9
32777/tcp open  sometimes-rpc17
32778/tcp open  sometimes-rpc19
32786/tcp open  sometimes-rpc25

---

### Post by lykwydchykyn on 2009-12-18
Well, based on that port scan the solaris box would appear to be running rsh (port 514), along with ftp and nfs.   You might have better luck trying to ftp into it, or seeing what filesystems are exported.

If you need to install rshd on Ubuntu, just use the package manager (that's Synaptic, if you're on default ubuntu desktop) to install the rsh-server package.

You might be better off just installing the rsh-client package and seeing if the Ubuntu machine can do rcp from the Solaris machine.  rshd is not a service I'd want running on my Ubuntu machine, I'll tell you that.

---

