---
title: "Cannot join NIS Domain"
date: 2006-05-30
forum: General Help
---

### Post by bnj on 2006-05-30
Hello,
I have great difficulties to join a NIS domain using Ubuntu.
When I try to logon, it tells me "incorrect password or username".
I have followed the instructions given on [https://wiki.ubuntu.com/SettingUpNISHowTo](https://wiki.ubuntu.com/SettingUpNISHowTo)

My /etc/hosts.deny file is empty.
My /etc/hosts.allow file contains these two lines:
```
portmap : ALL: LOCAL @.mydomain.ch
portmap : ip.of.my.nis.server
```

When I go to a folder that is mounted via NFS, I get the following error repeated several times:
YPBINDPROC_DOMAIN: Domain not bound
However, I can browse the folder.

The NIS server works, because I use it on other machines (running SuSE).

I have no idea what to do. Any suggestion? What could I check? What could I do? I would love to compare the setup between my ubuntu box and my suse boxes, but I do not know which files to check.

Besides, I read on google that some people having the same problem solved it by deactivating a firewall. How can I know if any firewall is turned on on my machine and how to turn it off?

Thank you.

---

