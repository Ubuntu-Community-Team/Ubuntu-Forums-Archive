---
title: "ssh server: how to kill inactive processes"
date: 2010-11-12
forum: General Help
---

### Post by linuxgr on 2010-11-12
hi all!

Here's my problem:

I have placed a script in /etc/network/if-up.d/ that creates a reverse ssh tunnel with a host such as:

```
ssh -o ExitOnForwardFailure=yes -o TCPKeepAlive=no -L 9000:localhost:22 user@host
```

Problem is, if the device gets disconnected from the internet, then a process remains on the host. The more disconnects, the more processes.

Is there any way to have the process(tunnel) killed on the host should the device gets disconnected?

Thanks!


PS: what is the difference between -L and -R options in ssh?

---

