---
title: "Public Key is not available"
date: 2006-03-31
forum: General Help
---

### Post by CharlieC on 2006-03-31
I am trying to add a repository. When I apt-get update I get the following error:

GPG error: [http://repos.knio.it](http://repos.knio.it) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CBE5831435A92053
W: You may want to run apt-get update to correct these problems

I have been googling and nothing seems to work
Does anyone have any suggestions how I could cure this?

TIA
Charlie

---

### Post by seppo on 2006-03-31
Hi,

You've to trust his repository key:

> 
wget [http://repos.knio.it/key.asc](http://repos.knio.it/key.asc)
apt-key add key.asc


---

### Post by lcg on 2006-03-31
[QUOTE=CharlieC]I am trying to add a repository. When I apt-get update I get the following error:

GPG error: [http://repos.knio.it](http://repos.knio.it) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CBE5831435A92053
W: You may want to run apt-get update to correct these problems

I have been googling and nothing seems to work
Does anyone have any suggestions how I could cure this?[/QUOTE]
Get the public key of the repository's maintainer and use 'apt-key add <keyfile>' to make it known to apt.

HTH,
Lars

---

### Post by CharlieC on 2006-03-31
Thank you, that did it

---

