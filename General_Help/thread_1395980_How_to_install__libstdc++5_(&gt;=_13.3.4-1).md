---
title: "How to install  libstdc++5 (&gt;= 1:3.3.4-1)?"
date: 2010-02-01
forum: General Help
---

### Post by TheSnook on 2010-02-01
I got some .deb files and when I try to install them Linux complains about " libstdc++5 (>= 1:3.3.4-1)" doesn't exist.

But how do I install it? I can't find this version in the packet manager.

---

### Post by hawthornso23 on 2010-02-01
> **TheSnook said:**
> I got some .deb files and when I try to install them Linux complains about " libstdc++5 (>= 1:3.3.4-1)" doesn't exist.

But how do I install it? I can't find this version in the packet manager.

You've run into this bug

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/431091](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/431091)

As these libraries are not in the karmic repositary you have to install them yourself. There are several ways to do it most of which are discussed in the bug report linked above. The one in comment number 17 works well.

You might want to contribute to the bug discussion. These libraries were deliberately removed (they are present in debian, and it actually took effort to remove them) for reasons that seem very weak to me. Their removal has broken a LOT of proprietary applications compiled against the old libraries. It broke my ut2004 for example. 

If you've got the source you can just recompile against libstdc++6 to fix the problem. But you can't do that for any proprietary application using this library. The person who removed them seems hostile to the idea of running proprietary applications on ubuntu.

Personally I think someone involved in policy needs to look at the processes that went into this decision.

---

### Post by TheSnook on 2010-02-02
> **hawthornso23 said:**
> You've run into this bug

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/431091](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/431091)

.....


Thank you so much! I'm a Linux noob but I finally got my printer working, but it was a lot harder than the last time I installed the drivers, 1-2 years ago.

I don't have any idea why they did remove this lib but it seems to create a lot of problems for new people like me, but your link helped. Thanks. :)

I will have a look at that bug discussion.

---

