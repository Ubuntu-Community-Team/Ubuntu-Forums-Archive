---
title: "How do I know which directory a package being installed?"
date: 2009-08-21
forum: General Help
---

### Post by cpthk on 2009-08-21
I usually do apt-get install to install packages, but some libraries or development files I need to know where did it installed? Is there any command I could find out?

Thanks.

---

### Post by zvacet on 2009-08-21
You can try with 

```
locate package_name
```

or 

```
sudo find / -name package_name
```

---

### Post by slakkie on 2009-08-21
dpkg -L package

Shows you the location of all files which are installed.

---

### Post by kpkeerthi on 2009-08-21
Or go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/), search for a package. In the package detail page, scroll to bottom of the page where the list of package files are detailed.

---

