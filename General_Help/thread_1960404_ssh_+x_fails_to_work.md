---
title: "ssh +x fails to work"
date: 2012-04-17
forum: General Help
---

### Post by satimis on 2012-04-17
Hi all,

$ ssh +x 192.168.0.10
worked previously forwarding X to local PC

Suddenly;
$ ssh +x 192.168.0.10```

ssh: Could not resolve hostname +x: Name or service not known

```

However
$ ssh 192.168.0.10
still works connecting the remote PC

$ sudo stop ssh
ssh stop/waiting

$ sudo start ssh
ssh start/running, process 6027

couldn't solve the problem.  Pls help.  TIA

satimis

---

### Post by rajtendulkar on 2012-04-17
it should be 
```

ssh -X 192.168.0.10

```

---

### Post by satimis on 2012-04-17
> **rajtendulkar said:**
> it should be 
```

ssh -X 192.168.0.10

```
Oh sorry, it was my typing mistake.

Yes, it works.  Tks

---

### Post by satimis on 2012-04-17
Furthermore:

Started X forwarding on 2nd workplace. But it was forwarded to all other 3 workplaces simultaneously.

Is there any way restricting X to be forwarded to only one workplace, i.e. the current working one. 

TIA

satimis

---

