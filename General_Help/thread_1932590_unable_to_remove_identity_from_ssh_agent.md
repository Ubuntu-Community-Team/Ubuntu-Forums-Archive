---
title: "unable to remove identity from ssh agent"
date: 2012-02-27
forum: General Help
---

### Post by peter360 on 2012-02-27
Looks like ssh-add -D removes all identities except the default (~/.ssh/id_rsa).  On my desktop running 11.10:

$ ssh-add -D
All identities removed.
$ ssh-add -l
2048 b3:69:ca:26:f6:15:fc:36:19:7a:ac:bc:98:98:3c:86 key-name (RSA)

where key-name is the name in ~/.ssh/id_rsa.pub

Is this expected?  I tried ssh-add -D on my macbook and it doesn't seem to have this problem.

---

