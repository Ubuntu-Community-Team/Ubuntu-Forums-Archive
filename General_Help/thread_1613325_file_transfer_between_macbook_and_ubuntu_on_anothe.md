---
title: "file transfer between macbook and ubuntu on another PC"
date: 2010-11-04
forum: General Help
---

### Post by damonkashu on 2010-11-04
I have Ubuntu running in VMware workstation on my PC, and a macbook pro running snow leopard. Both are connected to the same Apple Airport (PC connected by CAT5, Macbook on wifi)

I have some files in Ubuntu I want to get over to the macbook, can this be achieved via FTP or scp? What would be the best way to go about doing this? I hope the answer isn't "USB flash drive" :X

---

### Post by aspedisca on 2010-11-04
scp should work just fine and get it done.

---

### Post by damonkashu on 2010-11-04
I'm aware I can ssh and scp to the macbook by activating remote login on the mac, but how would I do it the other way around? That is. scp files from the macbook to ubuntu (on vmware)?

---

### Post by damonkashu on 2010-11-04
bump

---

### Post by btindie on 2010-11-04
Have you got openssh-server installed on your ubuntu machine?
```
dpkg -l openssh-server
```If not, then install that first.
```
sudo apt-get install openssh-server
```
You can check that it's listening with
```
netstat -nptl | grep sshd
```Have you tried scp'ing the files from your mac yet? If that failed then it may be either that the hostname doesn't resolve, in which case use the IP address, or the IP address assigned by VMWare is not routable - it's doing NAT.

Change the interface configuration to bridged if you've still got problem then it will get an address in the same subnet as your mac.

Have you tried using NFS for sharing your files?

---

