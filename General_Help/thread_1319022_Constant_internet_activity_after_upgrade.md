---
title: "Constant internet activity after upgrade"
date: 2009-11-08
forum: General Help
---

### Post by MeKino on 2009-11-08
Hi,

I have been monitoring my internet activity (uploads/downloads) with a conky script for some time now and I have noticed that since upgrading to karmic there is an awful lot more activity even when my web browser is inactive.

There is a constant stream of uploading & downloading going on and I don't know why!

So, two questions:

1. Does anybody know what's going on here?
2. Is there a way to start\stop internet connection via the terminal?

Thanks in advance.

I've just found the solution to Q2 - there is an icon for wired network connection on the top toolbar which I can enable\disable - cool!

---

### Post by ww711 on 2009-11-08
> **MeKino said:**
> Hi,

I have been monitoring my internet activity (uploads/downloads) with a conky script for some time now and I have noticed that since upgrading to karmic there is an awful lot more activity even when my web browser is inactive.

There is a constant stream of uploading & downloading going on and I don't know why!

So, two questions:

1. Does anybody know what's going on here?
2. Is there a way to start\stop internet connection via the terminal?

Thanks in advance.

I've just found the solution to Q2 - there is an icon for wired network connection on the top toolbar which I can enable\disable - cool!

In a terminal, when you are connected, run

```
netstat -natp
```

via terminal, this will give you a list of active/open connections with IPs against applications running.

---

