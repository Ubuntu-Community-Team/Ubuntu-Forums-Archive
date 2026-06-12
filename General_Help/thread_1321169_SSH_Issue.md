---
title: "SSH Issue"
date: 2009-11-09
forum: General Help
---

### Post by lewisforlife on 2009-11-09
I am having an issue with OpenSSH.  Previously I was using password authentication, I now want to beef up security so I turned off password authentication and want to use RSA public and private key authentication.  I created a public and private key pair on the server with:

```
ssh-keygen -f ~/.ssh/id_rsa -t rsa
```

I copied the public key to one of my client computers and ran:

```
cat id_rsa.pub > ~/.ssh/authorized_keys
```

to copy the contents to my authorized keys.  I made sure that:

```
PubkeyAuthentication yes
RSAAuthentication yes
```

were both set and I restarted my ssh server.  Still when I try to connect from the client computer I get the following:

```
david@david-laptop:~$ ssh david@192.168.1.102
Permission denied (publickey).

```

Does anyone know why this is happening?  What can I look at to try to troubleshoot this issue?

---

### Post by falconindy on 2009-11-09
Does your config correctly specify the location of the authorized_keys file?

---

### Post by lewisforlife on 2009-11-09
Yes, I figured out the problem.  I needed to create the RSA key on my client, and add the public key to my server, but what I did is created the keys on my server, and added the public key to my client.  Once I added the public key to my server this fixed the problem.  Thanks for your help.

---

