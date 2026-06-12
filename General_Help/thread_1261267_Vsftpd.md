---
title: "Vsftpd"
date: 2009-09-08
forum: General Help
---

### Post by godfreysikha on 2009-09-08
***********************************************
I am trying to use an machine running latest Ubuntu version to share files with friends. So, installed vsftpd on Ubuntu, as per the documentation and set up for local users to access the files. Now, how do I access these folders from other computers both within the network and outside the local network.Able to connect from a computer within a local network, but doesnt seem to connect from a computer from outside the network. Does anybody have suggestions for getting around this problem.
thanks!

---

### Post by eric3_14159 on 2009-10-08
I believe that you can connect using the users' username and normal password. This should give you access to that user's files.

The problem with computers outside the network is that you are probably behind a NAT. Your computer most likely does not have an external IP address. You'll have to look up port forwarding in whatever you are using to connect your local network to the Internet.

---

### Post by carnagex420x on 2009-10-08
Agreed, if you can login locally, you just need to set up your network for remote availability. All you should need is to forward a port, and I would setup DynDNS to make it easier as well (instead of remembering an IP(that probably isn't static)).

---

