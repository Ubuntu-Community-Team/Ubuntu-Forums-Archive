---
title: "I have no sshd_config file"
date: 2012-03-13
forum: General Help
---

### Post by gishaust on 2012-03-13
I have been having trouble with ssh on my server could get any access I just typed the followin
```

sudo find / -name  sshd_config 

```

and got the following
/usr/share/doc/openssh_client/examples/sshd_config

this is the only reference I have on my whole server. I have installed it twice 

```

sudo apt-get install ssh

```

and it tell me I have the latest version my question is simple how do I purge this thing complete from my system so I can reinstall it?

---

### Post by Habitual on 2012-03-13
```
sudo apt-get install openssh-server
```

---

