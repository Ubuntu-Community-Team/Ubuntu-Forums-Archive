---
title: "Getting fixes from Launchpad"
date: 2011-12-31
forum: General Help
---

### Post by gregalynch on 2011-12-31
This is probably something I should know, but, when a fix is listed as 'released' on Launchpad, how do you actually install it?  Do these always show up in update manager, and if so, how long after they are marked as fix released to they appear?

For example, I have this bug:
 
[https://bugs.launchpad.net/unity/+bug/741995](https://bugs.launchpad.net/unity/+bug/741995)

And it says that a fix (for BAMF, at least) is released.  I haven't yet seen this show up in update manager (though I may have missed it).  How do I go about actually getting the package that was released (or finding out that I already have it and it just didn't fix the problem)?

Thanks

---

### Post by BC59 on 2011-12-31
As I see the new package you mention bamf - 0.2.104-0ubuntu2, is for the next version of Ubuntu, the 12.04. 
Maybe you have to wait until an Oneiric solution is published.

---

### Post by gregalynch on 2011-12-31
ah, didn't see that.  Still, though, if it were for oneiric how would I go about getting it?

---

### Post by BC59 on 2011-12-31
They should prepare an upgrade sooner or later, so if you install them periodically, you will not miss it.

---

### Post by MG&amp;TL on 2011-12-31
Launchpad hosts two kinds of fixes and packages:

1. PPA/builds of programs. These you can just install when somebody bothers to build them for Oneiric.

2. Bzr branches. These will give you a bzr branch (source package) which you can presumably build and/or install.

I don't know what BAMF is, but if it's something 'core' then I would just wait until Precise, or an update comes through.

---

