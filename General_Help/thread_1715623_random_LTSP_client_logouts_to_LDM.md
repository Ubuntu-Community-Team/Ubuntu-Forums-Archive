---
title: "random LTSP client logouts to LDM"
date: 2011-03-27
forum: General Help
---

### Post by kfleten on 2011-03-27
Hi 

I have experienced random LTSP client logouts to LDM on different Ubuntu systems for a while. Some investigation points me in the direction of Xorg using to much memory in Firefox, but the problem also occasionaly occur in Openoffice and other applications.

In the thread [http://www.mail-archive.com/ltsp-discuss@lists.sourceforge.net/msg38549.html](http://www.mail-archive.com/ltsp-discuss@lists.sourceforge.net/msg38549.html), it seems like setting MOZ_DISABLE_IMAGE_OPTIMIZE=1 in /etc/profile could probably solve the problem when using Firefox.

But I would like to solve the problem no matter what application the users launch ?

Is there a general Xorg RAM limiting option for LTSP clients in any config files ?

---

