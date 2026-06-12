---
title: "VirtualBox - Kubuntu - Is your's working?"
date: 2009-11-26
forum: General Help
---

### Post by Roasted on 2009-11-26
I tried installing the latest deb package of VirtualBox from their web site.

I am running Kubuntu Jaunty 9.04 64 bit - so I grabbed the Ubuntu Jaunty AMD64 package. When I try to install it, it errors out simply saying "Sorry, an error occured."

Okay, great. Now I'm clueless. How do I fix this? This is the same package I installed on Ubuntu Jaunty 9.04 64 bit on this same pc, so I'm not sure why it's giving me a hard time in Kubuntu. I mean, I got the right package - didn't I?

EDIT - I ended up opening the deb package with GDebi instead of KPackageKit like it defaulted to. It worked. What was up with KPackageKit?? Has anybody installed Virtualbox through the deb package with KPackageKit without errors?

---

### Post by amingv on 2009-11-27
Although you have already solved your issue, I guess I may be able to explain the reason it wasn't working.

It has happened to me before that for some reason KPackageKit would detect the deb had unmet dependencies, but would not install them and just yield an error.
If I installed dependencies manually, KPackageKit would install with no complaints.
This problem hasn't occurred so far in Karmic, so I guess it was fixed.

I generally just add the VirtualBox repo to my sources.list, though, and let it sort itself out.

---

### Post by peterroots on 2009-12-07
Yes the unmet dependency issue does not occur in Karmic though it only helpfully says there are unmet dependencies, not what they are.  Where it does fail though (and this may be a problem with VB) is that if you should be prompted to agree a EUL (which I thing VB does ask you for) KpackageKit does not pass this on to you and just drops out with no explanation.

---

