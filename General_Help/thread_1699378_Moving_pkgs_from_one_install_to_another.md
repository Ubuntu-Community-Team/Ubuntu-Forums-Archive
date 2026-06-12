---
title: "Moving pkgs from one install to another"
date: 2011-03-03
forum: General Help
---

### Post by Trippster413 on 2011-03-03
Just setup a new install and want to get the packages from the other system over to the new system without spending all day looking them up and apt-get'ing them. I am so ridiculously noobish when it comes to ubuntu and linux in general but I'm sure there is a quick fix or someone can point me in the right direction.

Have ssh installed on both machines and quick access to both but the couple places that I have searched on the internet have spooled up nothing that has worked.

Thanks. :)


**cliffs: new install needs old packages, easiest way to get them to the new system?**

---

### Post by oldos2er on 2011-03-03
Downloaded packages live in /var/cache/apt/archives; unless you've cleaned them out they should all still be there. I'm assuming you're running the same version of Ubuntu on both machines.

---

