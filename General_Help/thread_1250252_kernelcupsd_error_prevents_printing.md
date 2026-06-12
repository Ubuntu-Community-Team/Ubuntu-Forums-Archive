---
title: "kernel/cupsd error prevents printing"
date: 2009-08-26
forum: General Help
---

### Post by ajaustin on 2009-08-26
I'm not sure since when but as of now I can only print one page of any document.  Any subsequent page seems to give the following kernel error message:-

> Aug 26 15:12:40 ubuntu kernel: [  973.702142] audit(1251292360.846:28): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=31075 profile="/usr/sbin/cupsd" namespace="default"

It all used to work fine a little while back.

Any ideas would be welcome, thanks.

Tony

---

### Post by MartinEve on 2009-08-26
What kernel versions are you using?

```

uname -a

```

If you are having problems, you could try upgrading to the latest if you haven't, which is, in jaunty stable 2.6.28-15-generic.

---

### Post by ajaustin on 2009-08-27
I am running a fully updated Hardy Heron LTS, obviously I wouldn't want to stray from the released version as this defeats the object of using LTS.

Kernel I'm using is:-

Linux ubuntu 2.6.24-24-386 #1 Tue Aug 18 16:24:26 UTC 2009 i686 GNU/Linux

Any ideas what the error message means.

Thanks for your help.

Tony

---

### Post by ajaustin on 2009-09-16
I just installed the LTS kernel update:-

Linux ubuntu 2.6.24-24-386 #1 Sat Aug 22 00:32:28 UTC 2009 i686 GNU/Linux

it didn't solve the problem.

HOWEVER!

I went to System/Adminsitration/Printing and chose a different Postscript driver and I can now print more than just one page.

---

