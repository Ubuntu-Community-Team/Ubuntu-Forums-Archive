---
title: "Help with ssh public keys: hide username."
date: 2011-11-10
forum: General Help
---

### Post by staticd on 2011-11-10
In an ssh public key file, the username and host of the machine from which the login is attempted is exposed.

```

$cat ~.ssh/id_rsa.pub
ssh-rsa blah-garbage-random localuser@client.hostname

```

Is there some way of preventing the username(of the client) from being publicly visible when giving out a public key to a server?

---

### Post by Habitual on 2011-11-10
> **staticd said:**
> In an ssh public key file, the username and host of the machine from which the login is attempted is exposed.

```

$cat ~.ssh/id_rsa.pub
ssh-rsa blah-garbage-random localuser@client.hostname

```

Is there some way of preventing the username(of the client) from being publicly visible when giving out a public key to a server?

terminal > 
```
chmod 600 ~.ssh/id_rsa.pub
```

I think, but am not certain that the "localuser@client.hostname" is even needed in the /root/.ssh/authorized_key* file. But don't bet the farm on what I know.

Someone else will chime in.

---

### Post by staticd on 2011-11-12
yup in v2 rsa the coomnt at the end can be edited to include anything

---

