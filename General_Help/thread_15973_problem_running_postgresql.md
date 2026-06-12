---
title: "problem running postgresql"
date: 2005-02-18
forum: General Help
---

### Post by now departed on 2005-02-18
Hi,
I used synaptic to install postgresql. It worked fine (at least I thought). The postmaster is automatically launched at boot time. Great. The thing is I am able as user "pascal" to create a cluster (see postgresql terminology) with the initdb command. When I then want to create a database I get the following message :"
createdb: céchec lors de la connexion à la base de données template1: FATAL:  user "pascal" does not exist."
I don't see what I did wrong. With the previous distrib I used (mdk9.2) the rpm manager did it right and I was able to launch the postmaster, initiate a cluster and create a db and so on.
I think here that the postmaster is started and then "owned" in some way by root (which from what I understand doesn't exist as such). But even with the sudo createdb command, it does not recognize root as a user.

Help welcome.

Thanx

---

