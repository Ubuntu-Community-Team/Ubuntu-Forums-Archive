---
title: "ssh"
date: 2011-09-20
forum: General Help
---

### Post by venicequeen7706 on 2011-09-20
I'm trying to ssh between to laptops to transfer files between them. One is an HP with 10.1o and the other is an Alienware with 11.10 beta. I can ssh from the HP to the alienware, but it doesn't work in reverse. Each has the other's rsa_pub key in the authorized key files. When I try from the alienware to the HP nothing happens.

Any Ideas?

---

### Post by brucehohl on 2011-09-20
Do you have openssh-server installed and running on "HP"?

Can you ping "HP"?

---

### Post by raja.genupula on 2011-09-20
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

[http://ekkescorner.wordpress.com/blog-series/git-mercurial/step-by-step-ssh-on-osx-ubuntu-and-windows/](http://ekkescorner.wordpress.com/blog-series/git-mercurial/step-by-step-ssh-on-osx-ubuntu-and-windows/)


going to help you.
All the Best

---

### Post by venicequeen7706 on 2011-09-20
yes to both

---

### Post by patryk77 on 2011-09-20
Define "nothing happens"... Times out?

Check if you don't have any iptables rules blocking it:
iptables -L

Or another firewall

Can you ssh from the HP machine to itself?

ssh localhost

---

### Post by venicequeen7706 on 2011-09-20
> **patryk77 said:**
> Define "nothing happens"... Times out?

Check if you don't have any iptables rules blocking it:
iptables -L

Or another firewall

Can you ssh from the HP machine to itself?

ssh localhost
Apparently it was a firewall setting on the HP. 

Thanks everyone

---

