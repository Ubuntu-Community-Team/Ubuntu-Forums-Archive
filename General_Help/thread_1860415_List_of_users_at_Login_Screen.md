---
title: "List of users at Login Screen"
date: 2011-10-14
forum: General Help
---

### Post by tps on 2011-10-14
A few friends of mine use Ubuntu at their jobs, but the IT guys don't like it. Today, they upgraded and have found there doesn't seem to be a way to disable the list of user accounts on the systems at the login screen. This is against their local security policies, and they were given 48 hours to get it fixed, or remove the OS. Can someone point out to me where this can be changed?

Thanks,
Tim

---

### Post by Seq on 2011-10-14
> **tps said:**
> A few friends of mine use Ubuntu at their jobs, but the IT guys don't like it. Today, they upgraded and have found there doesn't seem to be a way to disable the list of user accounts on the systems at the login screen. This is against their local security policies, and they were given 48 hours to get it fixed, or remove the OS. Can someone point out to me where this can be changed?

Thanks,
Tim

I assume you had gdm configured to display a plain username & password box without the graphical selector?

You'll have to install gdm to get the old login manager back.

[http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html](http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html)

---

### Post by IWantFroyo on 2011-10-14
You can use LightDM, SLiM or KDM. Or you could edit the GDM theme (I forgot the tool you use, though).

My recommendation: SLiM.

---

