---
title: "Can Ubuntu packages conflict with Debian packages?"
date: 2011-05-03
forum: General Help
---

### Post by Durduran on 2011-05-03
Hello,

I want to use apt-cacher to cache packages for me and I would like to know whether it is possible that there are going to be packages with the same name but different content between Ubuntu and Debian. I remember reading that whenever a Debian package is modified in any way by the Ubuntu team they append "ubuntu" to its version so it shouldn't conflict. But I want to make sure that this is correct and I did not misunderstood.

Thanks

---

### Post by dcstar on 2011-05-04
> **Durduran said:**
> Hello,

I want to use apt-cacher to cache packages for me and **I would like to know whether it is possible that there are going to be packages with the same name but different content between Ubuntu and Debian.**

Yes, do not install Debian packages unless **you** are 100% sure there won't be any problems.

---

### Post by Durduran on 2011-05-04
Thanks but that wasn't really my concern, the issue is that apt-cacher puts all cached packages in the same directory so if I configure Debian and Ubuntu systems both to use the same apt-cacher server it could result in cached packages from one system to overwrite packages from the other (as it would try to put them in the same directory and if they have the same filename but different content, that would cause trouble).

Anyway, I set it up nonetheless ... I do not think Ubuntu and Debian have any packages that are named the same but different. All Ubuntu modified packages should have "ubuntu" in the version and therefore different filename so I think it should work.

---

