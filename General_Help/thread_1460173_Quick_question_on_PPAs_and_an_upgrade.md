---
title: "Quick question on PPAs and an upgrade"
date: 2010-04-22
forum: General Help
---

### Post by MGMorden on 2010-04-22
Hey guys - I've got a quick question.  I'm currently running 9.10 and am anticipating upgrading to 10.04 when it is released next week.  I am however, running several packages from PPA's that were simply not working well at the versions included with 9.10 (I know specifically the 64-bit version of Flash and Wine are setup this way).

Since these installs are out of the scope of the official Ubuntu sources, how are these handled when I upgrade?  Are they removed?  

More importantly, since some of these packages were just installed as a temporary fix until 10.04 came out, for some of them I'd like to remove the PPA version and reinstall the default version (since for several of them the 10.04 version has caught up to where it needs to be).  Is there any way to identify all packages installed from PPA's on the system?  

Thanks.

---

### Post by thomasaaron on 2010-04-22
You should be able to go to System > Admin > Software Sources and identify the PPA packages and disable them. Then do your upgrade and test your system. 

Then, if necessary, you should be able to re-enable those repos as you see fit.

---

