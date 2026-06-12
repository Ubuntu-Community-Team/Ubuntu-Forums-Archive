---
title: "sshd not working"
date: 2010-01-20
forum: General Help
---

### Post by pjssilva on 2010-01-20
Hello,

Since today my sshd stopped working properly. Most of the time I get:

    [pjssilva@catirina:~]$ ssh localhost
    ssh_exchange_identification: Connection closed by remote host

and only in a few attempts I can connect (seems random).

My /etc/hosts.deny and /etc/hosts.allow are both empty.

I am using 9.10 64 bit.

Any hints?

---

### Post by n0dix on 2010-01-20
Why localhost?? You can use ssh for more than that.
Use ssh with another computer.
Localhost = yourself

---

### Post by pjssilva on 2010-01-20
Hmm... It went back working again by itself (which is not a confortable feature). I was reading on the subject on the internet and I have a hint on what may have happened. It seems that our network is experimenting problems with DNS. Maybe the sshd was not being able to lookup the dns from my machine (and other machines in the same network, as I tried to ssh from them) and hence it failed.

Anyhow I can not know for sure.

---

### Post by zollie on 2010-01-20
ssh localhost should work just fine.  This would never have anything to do with DNS, provided your **/etc/hosts** is setup correctly.

---

