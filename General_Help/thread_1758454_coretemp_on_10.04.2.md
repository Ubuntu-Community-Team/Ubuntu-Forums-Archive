---
title: "coretemp on 10.04.2"
date: 2011-05-14
forum: General Help
---

### Post by RCSub on 2011-05-14
Hi all
 
I have just installed a ubuntu server 10.04.2 64-bit on a Core-i5 based system.
 
When I try to "modprobe coretemp" i get something with "FATAL: Error ... No such device". I suspect it is because the coretemp module is outdated, because it worked in 10.10 (which had a reboot bug, therefore installed LTS). 
 
How do I install a newer version of coretemp?
 
Any help would be appreciated
 
RCSub

---

### Post by RCSub on 2011-05-15
Hi everyone
 
First I tried the following:
```
 
apt-get update
apt-get upgrade

```
 
Still no progress. Then I updated to : [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)
and again
```
 
apt-get update
apt-get upgrade

```
 
Still no progress
So I updated to [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/)
and again 
```
 
apt-get update
apt-get upgrade

```
 
And it worked :wink:
I am using the machine as a router and dhcp server based on dnsmasq, to route a PPTP and ssh connection to some windows machines, and this still works. So everything is good.
 
RCSub

---

