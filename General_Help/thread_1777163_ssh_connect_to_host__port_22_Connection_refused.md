---
title: "ssh :connect to host  port 22: Connection refused"
date: 2011-06-07
forum: General Help
---

### Post by electronforce on 2011-06-07
[root@****host ~]# scp -Cr /etc/yum 111.**.***.*6*:/etc/samba
ssh: connect to host 111.178.**.112 port 22: Connection refused
lost connection - What is the solution to this; trying to copy files over
the network.

---

### Post by iclestu on 2011-06-07
> **electronforce said:**
> [[COLOR=Red]**root**[/COLOR]@****host ~]# scp -Cr /etc/yum[COLOR=Red] 111[/COLOR].**.***.*6*:/etc/samba
ssh: connect[COLOR=Black] to [/COLOR][COLOR=Black]host 111.178.**.112 [/COLOR]port 22: Connection refused
lost connection - What is the solution to this; trying to copy files over
the network.

hmm - im not sure i know enough to say here but does the fact that you are using root from the client and specifying no username at server imply that you are trying to ssh into a root account on the server machine?? Guessing that causes all sorts of security implications they probably guard against...  cant you replace this with <SomeUserAccount>@111.**.??

---

