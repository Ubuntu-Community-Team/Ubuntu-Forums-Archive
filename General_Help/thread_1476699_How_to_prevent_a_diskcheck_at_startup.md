---
title: "How to prevent a diskcheck at startup"
date: 2010-05-08
forum: General Help
---

### Post by Rogierdg on 2010-05-08
I installed 10.04 LTS with great succes on my very old compac armada 500 laptop, but experience the problem of the hanging diskcheck at startup at regural intervals. I read this is a reported bug. My question is: is there any file or methot by which I can prevent diskcheck from running at startup, or put the frequency of running at a very very large number at least until the bug is fixed ?
Thanks

---

### Post by wilee-nilee on 2010-05-08
> **Rogierdg said:**
> I installed 10.04 LTS with great succes on my very old compac armada 500 laptop, but experience the problem of the hanging diskcheck at startup at regural intervals. I read this is a reported bug. My question is: is there any file or methot by which I can prevent diskcheck from running at startup, or put the frequency of running at a very very large number at least until the bug is fixed ?
Thanks

Find that bug report and post it. If you look at the screen it tells you how to cancel it. It runs every 20 boots just let it run at least on occasion.

---

### Post by Rogierdg on 2010-05-08
Here is the post for the related bug reports

Related bug reports:
[https://bugs.launchpad.net/ubuntu/+s...ll/+bug/571707]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571707")
[https://bugs.launchpad.net/ubuntu/+s...th/+bug/572786]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/572786")

My question actually was: can I prevent startup to force a FSCK by editing a file or a list ? I am pretty much capable of running a filecheck regulary at my own demand and do not like this to be forced on me every 20 or so boots. Else can I increase this number to lets say 1000 or so?
Thanks

---

### Post by rnerwein on 2010-05-08
> **Rogierdg said:**
> I installed 10.04 LTS with great succes on my very old compac armada 500 laptop, but experience the problem of the hanging diskcheck at startup at regural intervals. I read this is a reported bug. My question is: is there any file or methot by which I can prevent diskcheck from running at startup, or put the frequency of running at a very very large number at least until the bug is fixed ?
Thanks

hi
you can use the command "tune2fs" to set the parameter for automatic fsck.
there are two options.
tune2fs -c max-mount-counts
and
tune2fs -C mount-count
for further information see: man tune2fs

both commands you have to run as "root"
and by the side --> that's  (mostely ) no bug !!!!
ciao   ;)

---

