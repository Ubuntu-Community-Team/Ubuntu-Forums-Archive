---
title: "Bind to AD libkadm55 is not in the repositories any longer"
date: 2012-02-08
forum: General Help
---

### Post by CheezItMan on 2012-02-08
Hello,

I'm trying to bind my server to our local AD domain, however following the directions at:

[here]("https://help.ubuntu.com/community/Kerberos#Client_Configuration")

I find that libkadm55 is no longer in the default repositories, how can I add it, or is there something wrong with the package?

I'm running 10.10

I do get:

> 
sudo apt-get install libkadm55
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libkadm55 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libkdb5-4 libgssrpc4

E: Package 'libkadm55' has no installation candidate



---

