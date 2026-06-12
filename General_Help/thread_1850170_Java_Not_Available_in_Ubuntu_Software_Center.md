---
title: "Java Not Available in Ubuntu Software Center"
date: 2011-09-25
forum: General Help
---

### Post by Prorator on 2011-09-25
I can't find Sun Java 6 JRE in the Ubuntu Repositories. 

This is a new Ubuntu 11.04 install, and the first I've had where Java hasn't shown up in the Software Center or Synaptic Package Manager.

Any help would be much appreciated. Thanks.

---

### Post by lisati on 2011-09-25
Does it show if you open up Synaptic and use the search function (NOT quick find) for sun-java6?

---

### Post by .... on 2011-09-26
> **lisati said:**
> Does it show if you open up Synaptic and use the search function (NOT quick find) for sun-java6?
One needs to enable the "Canonical partner" repo (and refresh or apt-get update) before sun-java packages are installable.
[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Canonical_Partner_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Canonical_Partner_Repositories)

---

### Post by mikewhatever on 2011-09-26
Sun Java used to be in the partner repository, until Oracle killed it.
[http://www.h-online.com/open/news/item/Oracle-retires-licence-for-distributing-its-Java-with-Linux-1332835.html](http://www.h-online.com/open/news/item/Oracle-retires-licence-for-distributing-its-Java-with-Linux-1332835.html)

You are welcome to check, but if it's still there, it will be gone soon.

---

### Post by .... on 2011-09-26
> **mikewhatever said:**
> Sun Java used to be in the partner repository, until Oracle killed it.
[http://www.h-online.com/open/news/item/Oracle-retires-licence-for-distributing-its-Java-with-Linux-1332835.html](http://www.h-online.com/open/news/item/Oracle-retires-licence-for-distributing-its-Java-with-Linux-1332835.html)

You are welcome to check, but if it's still there, it will be gone soon.
Yeah, but I thought sun-java6 was still in the partner repo in 11.04 and earlier. I think Ubuntu and other distros are now declaring openjdk and/or icedtea as "good enough" for users that aren't java devs.

---

### Post by mikewhatever on 2011-09-26
Well, the old java packages are still there:
[http://archive.canonical.com/pool/partner/s/sun-java6/](http://archive.canonical.com/pool/partner/s/sun-java6/)

---

### Post by Prorator on 2011-09-26
I ended up just going with OpenJDK, my sister needed it for minecraft and it seems to do the job.

I appreciate the help, thanks.

---

