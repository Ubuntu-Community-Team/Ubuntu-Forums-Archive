---
title: "How to install old repo's"
date: 2009-07-02
forum: General Help
---

### Post by Its Me on 2009-07-02
Hi 

It was recommend that I install a package from an older Ubuntu release that the current verison I have runnign now (currently: 9.04 Jaunty).  How do I get symatpic, or apt-get, to find these older repo's?

thanks

---

### Post by wojox on 2009-07-02
edit /etc/apt/sources.list
add what ever repo's where recommended.

---

### Post by Ptero-4 on 2009-07-02
if you need to install a package that was available in older versions of ubuntu (except the current LTS version) but is no longer available (f.e: ms-sys) you'll need to use 
```

old-releases.ubuntu.com 

```
instead of 
```

archive.ubuntu.com

```

---

### Post by Its Me on 2009-07-02
great... how do I get synaptic (or apt-get) to go to old-releases.ubuntu.com ?  I tried using Settings -> repositories -> Other,  but could not find old-releases.ubuntu.com.  What am I doing wrong?

---

### Post by Ptero-4 on 2009-11-03
> **Its Me said:**
> great... how do I get synaptic (or apt-get) to go to old-releases.ubuntu.com ?  I tried using Settings -> repositories -> Other,  but could not find old-releases.ubuntu.com.  What am I doing wrong?
You need to introduce that in the /etc/apt/sources.list replacing archive.ubuntu.com with old-releases.ubuntu.com in every line the former appears.

---

### Post by cariboo on 2009-11-03
Instead of changing your /etc/apt/sources.list you may find it easier to go to the [Ubuntu Package Search]("http://packages.ubuntu.com/") page.

---

