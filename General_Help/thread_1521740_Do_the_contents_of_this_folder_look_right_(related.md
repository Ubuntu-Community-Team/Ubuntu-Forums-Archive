---
title: "Do the contents of this folder look right? (related to SSH server)"
date: 2010-07-01
forum: General Help
---

### Post by mahela007 on 2010-07-01
I've installed an SSH server on my Ubuntu desktop version. From what I've gathered, there are two folders which contain stuff related to SSH.

One is ~/.ssh
The other is /etc/ssh/

Here is a list of the files contained in the latter folder i.e /etc/ssh . Should all these files be here? I have a feeling that the dsa and rsa files shouldn't...
```
User@Ubuntu:/etc/ssh$ ls
moduli      sshd_config       ssh_host_dsa_key.pub  ssh_host_rsa_key.pub
ssh_config  ssh_host_dsa_key  ssh_host_rsa_key

```
Could you please tell me why SSH has two folders? Is it that one of these folder is for the SSH client (which is installed by default on ubuntu) and the other for the SSH server?

---

### Post by mahela007 on 2010-07-01
bump

---

### Post by WorMzy on 2010-07-01
I've never used it, but I'm guessing that if you run the service as a daemon, it'll look at the contents of /etc/ssh, if you run the service as a process, it'll look at the contents of ~/.ssh.

---

### Post by marshmallow1304 on 2010-07-01
Those are the server's keys; the client gets a copy of the public key during the first connect and stores it.  Then, every time the client reconnects, its copy is matched against the private key on the server.  If there's a mismatch, the client warns the user that the key has changed and that there's probably something fishy going on.

The keys kept in ~/.ssh are the user's keys, used to authenticate logins.

---

### Post by mahela007 on 2010-07-02
thanks.

---

