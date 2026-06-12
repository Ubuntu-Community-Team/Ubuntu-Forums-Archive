---
title: "How to Uninstall NX ?"
date: 2009-08-12
forum: General Help
---

### Post by antdgar on 2009-08-12
NX suddenly gave me errors ' cannot resume session'
so my friend said to re-install NX. He said to do this:

```
sudo apt-get remove nxserver
sudo apt-get remove nxnode
sudo apt-get remove nxclient
sudo rm -rf /etc/nxserver
sudo rm -rf /usr/NX

wget [http://64.34.161.181/download/3.3.0/...3.0-6_i386.deb]("http://64.34.161.181/download/3.3.0/Linux/nxclient_3.3.0-6_i386.deb")
wget [http://64.34.161.181/download/3.3.0/....0-17_i386.deb]("http://64.34.161.181/download/3.3.0/Linux/nxnode_3.3.0-17_i386.deb")
wget [http://64.34.161.181/download/3.3.0/....0-22_i386.deb]("http://64.34.161.181/download/3.3.0/Linux/FE/nxserver_3.3.0-22_i386.deb")

sudo dpkg -i nxclient_3.3.0-6_i386.deb
sudo dpkg -i nxnode_3.3.0-17_i386.deb
sudo dpkg -i nxserver_3.3.0-22_i386.deb
```The problem is even the first command does not work.
I get this:

E: Couldn't find package nxserver (or nxnode or nxclient) 
**any idea how to truly uninstall/reinstall?**

---

### Post by kribjo on 2011-11-27
First antdgar,

I hope you were able to fix your problem. This is two years later and you had no reponse. I just want to make a note for other users that I followed the instructions in this post to uninstall NX and did so succeccfully on Ubuntu 11.10 32-bit.

The only line that did not complete was sudo rm -rf /etc/nxserver. Obviuosly I did not have the file.

Regards,

Bjørn

---

