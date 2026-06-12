---
title: "Can't apt-get update after installing virtualbox"
date: 2010-06-15
forum: General Help
---

### Post by maddbaron on 2010-06-15
When i run sudo apt-get update the list runs but finished with this
> 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  404  Not Found
Fetched 7,667B in 2s (3,746B/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4D17133CFC5D50C5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 10975893E549B1AC
W: Failed to fetch [http://ppa.launchpad.net/nikolay-blohin/histwi/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/nikolay-blohin/histwi/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/yorba/pp/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/yorba/pp/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.




when I try to install a program via CLI I get this
> 
:~$ sudo add-apt-repository ppa:nikolay-blohin/histwi
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv D5DA4CE33ECE5AE838709C35CF32D8D5430711DE
gpg: requesting key 430711DE from hkp server keyserver.ubuntu.com
gpg: key 430711DE: "Launchpad Histwi" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
:~$ sudo apt-get install histwi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package histwi



I get this for different installs I want to do this is just the latest. 

Can anyone tell me how to fix this? 

Thanks in advance.

---

### Post by Chesamo on 2010-06-15
VirtualBox is not to blame, the PPA is not set up properly.

---

### Post by maddbaron on 2010-07-11
> **Chesamo said:**
> VirtualBox is not to blame, the PPA is not set up properly.

How do I set it up properly?

---

