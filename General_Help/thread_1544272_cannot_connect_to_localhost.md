---
title: "cannot connect to localhost"
date: 2010-08-02
forum: General Help
---

### Post by surrealillusions on 2010-08-02
Get the usual message of when theres network/connection problems:

Unable to connect
Firefox can't establish a connection to the server at localhost.

I could access it a few hours ago, but now I cant.....

Have not restarted the computer since, have not really done anything out of the ordinary either.

Why is it doing that and how to solve it? I have never got this problem before.

---

### Post by stlsaint on 2010-08-02
You trying to access a system on your LAN?

For giggles try:
```
sudo /etc/init.d/networking restart
```

---

### Post by surrealillusions on 2010-08-02
Localhost as in the apache server installed on this machine.

Did a restart of the computer and that appeared to fix it. But strange why it couldn't access the server on its own hard drive.

---

