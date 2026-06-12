---
title: "Enabling RSH in Ubuntu 11.10"
date: 2012-03-04
forum: General Help
---

### Post by GenericPlayer on 2012-03-04
It seems that the 'rsh' command in Ubuntu invokes 'ssh' instead. Is there a way to install/enable 'rsh' on Ubuntu? I googled it and the responses seem to revolve around how unsafe rsh is. That is not a concern for me as I am using this on a completely isolated private network of 2 machines.

I need this because I am running a program across the 2 machines that requires the ability to login without a password. I already tried ssh and its keygen method and its not working for me, password authentication is still being requested. If my memory of rsh is correct (last time i used was 10 years ago) all I need to do is define a .rhosts file. My only problem is that Ubuntu appears to be pushing me to ssh.


Is activating rsh in Ubuntu possible?

---

### Post by Bobhuber on 2012-03-04
Open synaptic package manager and type rsh.There are a couple of packages that may be what you are looking for

---

