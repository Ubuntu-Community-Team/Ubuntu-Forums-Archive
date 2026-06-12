---
title: "Help compiling sysvinit"
date: 2010-11-18
forum: General Help
---

### Post by BobMUK on 2010-11-18
Hi
I seem to be falling over bug 634460 in sysvinit ([https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/634460](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/634460)) which means every boot my filesystem needs recovery.  The recovery time isn't a problem, but the risk of losing data is (every time I see "orphan inodes deleted" I shiver :) )

Looks like it could take a while for the fix to hit the repositories as an update so I'd like to complie my own.

I've installed build dependancies and pulled a tarball from [http://svn.debian.org/wsvn/pkg-sysvinit](http://svn.debian.org/wsvn/pkg-sysvinit) - and now I'm stumped.  I'd assumed I'd need to run configure and make but there's no configure script so I'm stuck before I start.

Can anyone help?

---

