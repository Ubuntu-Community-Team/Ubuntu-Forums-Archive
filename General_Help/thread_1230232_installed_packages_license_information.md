---
title: "installed packages license information"
date: 2009-08-03
forum: General Help
---

### Post by tolik2525 on 2009-08-03
Hello!
Is there any way to get installed packages license information?
With dpkg-query i can only get package name, its description, ... but no word about its license type (gpl or bsd or something else). 
Thanks in advance.

---

### Post by nikhilk on 2009-08-03
> **tolik2525 said:**
> Hello!
Is there any way to get installed packages license information?
With dpkg-query i can only get package name, its description, ... but no word about its license type (gpl or bsd or something else). 
Thanks in advance.

If that package is from the official, default Ubuntu repositories, it is definitely open-source and has a comparable license (GPL, LGPL, Apache, BSD, MPL etc).
I don't think there is any special/dedicated placeholder in a .deb package for storing license information. You will have to check manually, by visiting the product website or contacting its developers etc, in case of doubt.

---

