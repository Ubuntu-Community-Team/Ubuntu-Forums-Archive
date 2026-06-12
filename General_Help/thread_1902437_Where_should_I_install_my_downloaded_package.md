---
title: "Where should I install my downloaded package"
date: 2011-12-30
forum: General Help
---

### Post by Sachin_ruk on 2011-12-30
Hi All,

I've downloaded Octave 3.4 (source code) and I want to install it. Question is where (note: I'm not concerned about how to install)? 

I don't want to pollute my home folder, so where do people usually install there downloaded packages. I guess I am comparing this to Windows version of 'Program files' folder.

Thanks,
Sachin

---

### Post by lisati on 2011-12-30
Downloads usually go in a special "Downloads" folder. If you're using the terminal (command line), you can use this to navigate to the folder:
```

cd ~/Downloads

```
Note: it's a capital D, not a lower-case d.

---

### Post by oldos2er on 2011-12-30
Once you've compiled it, if you run 'sudo make install' it generally goes to /usr/local/

---

### Post by Sachin_ruk on 2012-01-01
> **oldos2er said:**
> Once you've compiled it, if you run 'sudo make install' it generally goes to /usr/local/

I thought to do that you have to paste your folder into /usr/local first? but is this where as a linux user you would want your installed packages to be?

Thanks,
Sachin

---

### Post by oldos2er on 2012-01-01
That's the traditional place for user-compiled programs to go, see [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/Linux-Filesystem-Hierarchy.html#usr](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/Linux-Filesystem-Hierarchy.html#usr)

---

### Post by wildmanne39 on 2012-01-02
Hi, you can not think of the file system like you did in windows, ubuntu will put files where they need to go.
Thanks

---

