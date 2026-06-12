---
title: "failed to create queue file: no such file or directory"
date: 2012-04-27
forum: General Help
---

### Post by Azdour on 2012-04-27
Hi,

Before I start I'd like to outline what I am doing. I'm basically trying to get DRBL to work with Ubuntu 12.04. This is also increasing my knowledge of the underlying components of Ubuntu.

When a client boots it halts and I can see messages like this:

```
udevd[nnn]: failed to create queue file: No such file or directory
```

What little I have been able to find and understand through Google, it seems to me that there is a problem with the mounting of dev. Normally under Ubuntu 12.04 when I run mount I see the following dev entries:

```

udev on /dev type devtmpfs
devpts on /dev/pts type devpts

```

Can anyone else give me any ideas on this error message?

---

### Post by Azdour on 2012-05-04
Hi,

It looks like the latest unstable version of DRBL supports 12.04 so there is no need for me to keep looking into a solution.

---

