---
title: "about keyserver pls help me"
date: 2012-02-14
forum: General Help
---

### Post by lvshengming on 2012-02-14
i'm trying install openstack -swift componet
apt-get update

warning:
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en                                                            
Fetched 26.0 kB in 8s (3,166 B/s)                                                                                                  
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D21C2EC3D1B4472

can you tell me some available keyserver or some solution to resove this warning?
 
keyserver.ubuntu.com not available.

ths a lot

---

### Post by YesGood on 2012-02-24
Hi 

try with this command

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3D1B4472

and then run 
apt-get update.

Luck

---

