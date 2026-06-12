---
title: "Automatically accept license agreements using dpkg"
date: 2011-01-18
forum: General Help
---

### Post by awp2513_ on 2011-01-18
Hi,

I have a tar of .deb files that contains all the packages I need to install on a new system. I know that by using

```
dpkg -i *.deb
```

I can automatically install the packages without worrying about network connectivity, out-of-date packages, etc. (I really just want the my packages, not necessarily the most up to date ones).

There are several packages, however, that require that I accept a license agreement. I have been unable to find a dpkg parameter that will make it automatically respond "yes" when it needs to. I know there is an apt-get parameter like this, and my understanding is that apt-get invokes dpkg, so I have to assume there is one for dpkg.

I've been through the man page (maybe I missed it) and searched around, but all the answers I find are for apt-get.

Is there a parameter for dpkg that will allow me to automatically accept license agreements?

Thanks!

---

### Post by cccc on 2011-03-01
Have anyone find a solution, I'm interesting too?

---

